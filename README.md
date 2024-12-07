# Manage Subscriptions and RBAC

## Objective

In this lab, you learn about role-based access control. You learn how to use permissions and scopes to control what actions identities can and cannot perform. You also learn how to make subscription management easier using management groups.

*Ref 1: Architecture diagram*
![image](https://github.com/user-attachments/assets/2eeb6f22-f758-407d-b7ef-6722f633cacf)


### Job Skills Learned

- Implement management groups.
- Review and assign a built-in Azure role.
- Create a custom RBAC role.
- Monitor role assignments with the Activity Log.

### Tools Used

- Azure portal - https://portal.azure.com

## Steps

## Task 1: Implement Management Groups
In this task, you will create and configure management groups. Management groups are used to logically organize and segment subscriptions. They allow for RBAC and Azure Policy to be assigned and inherited to other management groups and subscriptions.

1.	Sign in to the Azure portal - https://portal.azure.com.
2.	Search for and select Microsoft Entra ID.
3.	In the Manage blade, select Properties.
4.	Review the Access management for Azure resources area. Ensure you can manage access to all Azure subscriptions and management groups in the tenant.
![image](https://github.com/user-attachments/assets/bce503bb-47d5-46f2-9fce-88c4a5716128)
 
5.	Search for and select Management groups.
6.	On the Management groups blade, click + Create.
7.	Create a management group with the following settings. Select Submit when you are done.
![image](https://github.com/user-attachments/assets/65ab5b65-de94-47c4-86d0-ff6d6ebeda12)
 
8.	Refresh the management group page to ensure your new management group displays. This may take a minute.
![image](https://github.com/user-attachments/assets/9c0a6294-bf2b-41a6-8c3d-3dcf70c952ef)

 
## Task 2: Review and assign a built-in Azure role
In this task, you will review the built-in roles and assign the VM Contributor role to a member of the Help Desk. Azure provides a large number of built-in roles.
1.	Select the az104-mg1 management group.
2.	Select the Access control (IAM) blade, and then the Roles tab.
3.	Scroll through the built-in role definitions that are available. View a role to get detailed information about the Permissions, JSON, and Assignments. You will often use owner, contributor, and reader.
![image](https://github.com/user-attachments/assets/73491d6c-80e0-4ea2-92fb-ed47a712974a)
 
4.	Select + Add, from the drop-down menu, select Add role assignment.
5.	On the Add role assignment blade, search for and select the Virtual Machine Contributor. The Virtual machine contributor role lets you manage virtual machines, but not access their operating system or manage the virtual network and storage account they are connected to. This is a good role for the Help Desk. Select Next.
6.	On the Members tab, Select Members.
7.	Search for and select the helpdesk group. Click Select.
![image](https://github.com/user-attachments/assets/f937cb51-329e-41c6-a1da-4646799ca54d)
 
8.	Click Review + assign twice to create the role assignment.
9.	Continue on the Access control (IAM) blade. On the Role assignments tab, confirm the helpdesk group has the Virtual Machine Contributor role.
![image](https://github.com/user-attachments/assets/15464054-28ee-4b58-9954-85b6f8602433)


## Task 3: Create a custom RBAC role
In this task, you will create a custom RBAC role. Custom roles are a core part of implementing the principle of least privilege for an environment. Built-in roles might have too many permissions for your scenario. We will also create a new role and remove permissions that are not necessary. Do you have a plan for managing overlapping permissions?
1.	Continue working on your management group. Navigate to the Access control (IAM) blade.
2.	Select + Add, from the drop-down menu, select Add custom role.
3.	On the Basics tab complete the configuration.
4.	For Baseline permissions, select Clone a role. In the Role to clone drop-down menu, select Support Request Contributor.
![image](https://github.com/user-attachments/assets/5ed99841-4de3-43f5-9916-3b36da106e61)
 
5.	Select Next to move to the Permissions tab, and then select + Exclude permissions.
6.	In the resource provider search field, enter .Support and select Microsoft.Support.
7.	In the list of permissions, place a checkbox next to Other: Registers Support Resource Provider and then select Add. The role should be updated to include this permission as a NotAction.
![image](https://github.com/user-attachments/assets/3333196a-52b9-4c53-bfed-4bf591b3e750)
 
8.	On the Assignable scopes tab, ensure your management group is listed, then click Next.
9.	Review the JSON for the Actions, NotActions, and AssignableScopes that are customized in the role.
![image](https://github.com/user-attachments/assets/16561e30-0254-4c99-9aa9-8ca5772fb87c)
10.	Select Review + Create, and then select Create.


## Task 4: Monitor role assignments with the Activity Log
In this task, you view the activity log to determine if anyone has created a new role.
1.	In the portal locate the az104-mg1 resource and select Activity log. The activity log provides insight into subscription-level events.
2.	Review the activites for role assignments. The activity log can be filtered for specific operations.
![image](https://github.com/user-attachments/assets/e39b855c-149b-43e2-9c8e-d30b7f68b8ae)

