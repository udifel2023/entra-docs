---
title: 'Tutorial: Configure Commbox for automatic user provisioning with Microsoft Entra ID'
description: Learn how to automatically provision and de-provision user accounts from Microsoft Entra ID to Commbox.

author: udifel2023
manager: yanivh
ms.service: entra-id
ms.subservice: saas-apps
ms.topic: tutorial
ms.date: 08/15/2024
ms.author: udifel2023

# Customer intent: As an IT administrator, I want to learn how to automatically provision and deprovision user accounts from Microsoft Entra ID to Commbox so that I can streamline the user management process and ensure that users have the appropriate access to Commbox.
---

# Tutorial: Configure Commbox for automatic user provisioning

This tutorial describes the steps you need to perform in both Commbox and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Commbox](http://www.commbox.io/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](~/identity/app-provisioning/user-provisioning.md). 


## Capabilities supported
> [!div class="checklist"]
> * Create users in Commbox.
> * Remove users in Commbox when they do not require access anymore.
> * Keep user attributes synchronized between Microsoft Entra ID and Commbox.
> * Provision groups and group memberships in Commbox.
> * [Single sign-on](./Commbox-tutorial.md) to Commbox (recommended)

## Prerequisites

The scenario outlined in this tutorial assumes that you already have the following prerequisites:

* [A Microsoft Entra tenant](~/identity-platform/quickstart-create-new-tenant.md). 
* One of the following roles: [Application Administrator](/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](/entra/fundamentals/users-default-permissions#owned-enterprise-applications). 
* A user account in Commbox with Admin rights.
* A Commbox tenant with the Professional plan or better enabled.

## Step 1: Plan your provisioning deployment
1. Learn about [how the provisioning service works](~/identity/app-provisioning/user-provisioning.md).
1. Determine who will be in [scope for provisioning](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).
1. Determine what data to [map between Microsoft Entra ID and Commbox](~/identity/app-provisioning/customize-application-attributes.md). 

<a name='step-2-configure-Commbox-to-support-provisioning-with-azure-ad'></a>

## Step 2: Configure Commbox to support provisioning with Microsoft Entra ID

1. Sign in to [Commbox Settings](https://manage.commbox.io/modules).
1. Click on the **API** module.
1. Click the **Settings** tab, and make sure Token Access is **enabled**.
1. Click the **Add API token** button to the right of **Active API Tokens**.The token is generated and displayed.
1. Enter an **API token description**.
1. **Copy** the token and paste it somewhere secure. Once you close this window, the full token will never be displayed again.
1. Click **Save** to return to the API page.If you click the token to reopen it, a truncated version of the token is displayed.

<a name='step-3-add-Commbox-from-the-azure-ad-application-gallery'></a>

## Step 3: Add Commbox from the Microsoft Entra application gallery

Add Commbox from the Microsoft Entra application gallery to start managing provisioning to Commbox. If you have previously setup Commbox for SSO, you can use the same application. However it is recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](~/identity/enterprise-apps/add-application-portal.md). 

## Step 4: Define who will be in scope for provisioning 

The Microsoft Entra provisioning service allows you to scope who will be provisioned based on assignment to the application and or based on attributes of the user / group. If you choose to scope who will be provisioned to your app based on assignment, you can use the following [steps](~/identity/enterprise-apps/assign-user-or-group-access-portal.md) to assign users and groups to the application. If you choose to scope who will be provisioned based solely on attributes of the user or group, you can use a scoping filter as described [here](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md). 

* Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

* If you need additional roles, you can [update the application manifest](~/identity-platform/howto-add-app-roles-in-apps.md) to add new roles.


## Step 5: Configure automatic user provisioning to Commbox

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Commbox based on user and/or group assignments in Microsoft Entra ID.

### Important tips for assigning users to Commbox

* Today, Commbox roles are automatically and dynamically populated in the Azure portal UI. Before you assign Commbox roles to users, make sure that an initial sync is completed against Commbox to retrieve the latest roles in your Commbox tenant.

* We recommend that you assign a single Microsoft Entra user to Commbox to test your initial automatic user provisioning configuration. You can assign additional users or groups later after the tests are successful.

* When you assign a user to Commbox, select any valid application-specific role, if available, in the assignment dialog box. Users with the **Default Access** role are excluded from provisioning.


<a name='configure-automatic-user-provisioning-for-Commbox-in-azure-ad'></a>

### Configure automatic user provisioning for Commbox in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](~/identity/role-based-access-control/permissions-reference.md#cloud-application-administrator).
1. Browse to **Identity** > **Applications** > **Enterprise applications**

	![Screenshot of Enterprise applications blade.](common/enterprise-applications.png)

1. In the applications list, select **Commbox**.

	![Screenshot of the Commbox link in the Applications list.](common/all-applications.png)

1. Select the **Provisioning** tab.

	![Screenshot of Provisioning tab.](common/provisioning.png)

1. Set the **Provisioning Mode** to **Automatic**.

	![Screenshot of Provisioning tab automatic.](common/provisioning-automatic.png)

1. Under the **Admin Credentials** section, input the admin username, secret token, and domain of your Commbox account. Examples of these values are:

   * In the **Admin Username** box, fill in the username of the admin account on your Commbox tenant. An example is admin@contoso.com.

   * In the **Secret Token** box, fill in the secret token as described in Step 6.

   * In the **Domain** box, fill in the subdomain of your Commbox tenant. For example, for an account with a tenant URL of `https://my-tenant.commbox.io`, your subdomain is **my-tenant**.

1. The secret token for your Commbox account can be generated by following steps mentioned in **Step 2** above.

1. After you fill in the boxes shown in Step 5, select **Test Connection** to make sure that Microsoft Entra ID can connect to Commbox. If the connection fails, make sure your Commbox account has admin permissions and try again.

	![Screenshot of Commbox Test Connection](./media/Zendesk-provisioning-tutorial/Zendesk19.png)

1. In the **Notification Email** box, enter the email address of the person or group to receive the provisioning error notifications. Select the **Send an email notification when a failure occurs** check box.

	![Screenshot of Commbox Notification Email](./media/Zendesk-provisioning-tutorial/Zendesk9.png)

1. Select **Save**.

1. Under the **Mappings** section, select **Synchronize Microsoft Entra users to Commbox**.

	![Screenshot of Commbox user synchronization](./media/Zendesk-provisioning-tutorial/Zendesk10.png)

1. Review the user attributes that are synchronized from Microsoft Entra ID to Commbox in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the user accounts in Commbox for update operations. To save any changes, select **Save**.

	![Screenshot of Commbox matching user attributes](./media/Zendesk-provisioning-tutorial/Zendesk11.png)

1. Under the **Mappings** section, select **Synchronize Microsoft Entra groups to Commbox**.

	![Screenshot of Commbox group synchronization](./media/Zendesk-provisioning-tutorial/Zendesk12.png)

1. Review the group attributes that are synchronized from Microsoft Entra ID to Commbox in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the groups in Commbox for update operations. To save any changes, select **Save**.

	![Screenshot of Commbox matching group attributes](./media/Zendesk-provisioning-tutorial/Zendesk13.png)

1. To configure scoping filters, follow the instructions in the [scoping filter tutorial](~/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

1. To enable the Microsoft Entra provisioning service for Commbox, in the **Settings** section, change **Provisioning Status** to **On**.

	![Screenshot of Commbox Provisioning Status](./media/Zendesk-provisioning-tutorial/Zendesk14.png)

1. Define the users or groups that you want to provision to Commbox. In the **Settings** section, select the values you want in **Scope**.

	![Screenshot of Commbox Scope](./media/Zendesk-provisioning-tutorial/Zendesk15.png)

1. When you're ready to provision, select **Save**.

	![Screenshot of Commbox Save](./media/Zendesk-provisioning-tutorial/Zendesk18.png)

This operation starts the initial synchronization of all users or groups defined in **Scope** in the **Settings** section. The initial sync takes longer to perform than later syncs. They occur approximately every 40 minutes as long as the Microsoft Entra provisioning service runs. 

You can use the **Synchronization Details** section to monitor progress and follow links to the provisioning activity report. The report describes all the actions performed by the Microsoft Entra provisioning service on Commbox.

For information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](~/identity/app-provisioning/check-status-user-account-provisioning.md).

## Connector limitations

* Commbox supports the use of groups for users with **Agent** roles only. For more information, see the [Commbox documentation](https://help.commbox.io/docs).

* When a custom role is assigned to a user or group, the Microsoft Entra automatic user provisioning service also assigns the default role **Agent**. Only Agents can be assigned a custom role. For more information, see the [Zendesk API documentation](https://www.commbox.io/api/). 

* Import of all roles will fail if any of the custom roles has a display name similar to the built in roles of "agent" or "end-user". To avoid this, ensure that none of the custom roles being imported has the above display names. 

## More resources

* [Managing user account provisioning for Enterprise Apps](~/identity/app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Microsoft Entra ID?](~/identity/enterprise-apps/what-is-single-sign-on.md)

## Next steps

* [Learn how to review logs and get reports on provisioning activity](~/identity/app-provisioning/check-status-user-account-provisioning.md)
