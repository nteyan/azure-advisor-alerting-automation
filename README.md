# Azure Advisor Alerting Deployment Automation with Azure Policy
##  What is Advisor?
Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments. It analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, Reliability (formerly called High availability), and security of your Azure resources.

With Advisor, you can:
- Get proactive, actionable, and personalized best practices recommendations.
- Improve the performance, security, and reliability of your resources, as you identify opportunities to reduce your overall Azure spend.
- Get recommendations with proposed actions inline.

You can access Advisor through the [Azure portal](https://aka.ms/azureadvisordashboard). Sign in to the [portal](https://portal.azure.com/), locate Advisor in the navigation menu, or search for it in the All services menu.

The Advisor dashboard displays personalized recommendations for all your subscriptions. You can apply filters to display recommendations for specific subscriptions and resource types. The recommendations are divided into five categories:
- Reliability (formerly called High Availability): To ensure and improve the continuity of your business-critical applications. For more information, see [Advisor Reliability recommendations](https://learn.microsoft.com/en-us/azure/advisor/advisor-high-availability-recommendations).
- Security: To detect threats and vulnerabilities that might lead to security breaches. For more information, see [Advisor Security recommendations](https://learn.microsoft.com/en-us/azure/advisor/advisor-security-recommendations).
- Performance: To improve the speed of your applications. For more information, see [Advisor Performance recommendations](https://learn.microsoft.com/en-us/azure/advisor/advisor-performance-recommendations).
- Cost: To optimize and reduce your overall Azure spending. For more information, see [Advisor Cost recommendations](https://learn.microsoft.com/en-us/azure/advisor/advisor-cost-recommendations).
- Operational Excellence: To help you achieve process and workflow efficiency, resource manageability and deployment best practices. For more information, see Advisor [Operational Excellence recommendations](https://learn.microsoft.com/en-us/azure/advisor/advisor-operational-excellence-recommendations).

![Advisor](https://learn.microsoft.com/en-us/azure/advisor/media/advisor-overview/advisor-dashboard.png)

You can click a category to display the list of recommendations within that category, and select a recommendation to learn more about it. You can also learn about actions that you can perform to take advantage of an opportunity or resolve an issue.

![Advisor](https://learn.microsoft.com/en-us/azure/advisor/media/advisor-overview/advisor-ha-category-example.png)

Select the recommended action for a recommendation to implement the recommendation. A simple interface will open that enables you to implement the recommendation or refer you to documentation that assists you with implementation. Once you implement a recommendation, it can take up to a day for Advisor to recognize that.

If you do not intend to take immediate action on a recommendation, you can postpone it for a specified time period or dismiss it. If you do not want to receive recommendations for a specific subscription or resource group, you can configure Advisor to only generate recommendations for specified subscriptions and resource groups.

##  About the Policy
1. To deploy this policy, you have to create an Action Group (the only requierement for this resource is to be deployed in the same tenant)
2. Once deployed, you will have to copy the resourceId. It should be something like this :
/subscriptions/<<SubscriptionID>>/resourceGroups/<ResourceGroupName>/providers/microsoft.insights/actionGroups/<ActionGroupName>
3. Copy/Paste the content of the [policy.json](https://github.com/nteyan/azure-advisor-alerting-automation/blob/main/policy.json) and create a new Policy Definition. The location for this policy definition can be a management group or a subscription. The "Role definitions" should be Contributor to allow the policy to create the resources.
4. Once deployed, Assign this policy to a management group or a subscription, fill the "resourceGroupName" and "actionGroupId" in the Parameters tab, don't forget to change the System assigned identity to your region and then select "Review + Create"