---
title: "Password Reset Loop"
description: "Troubleshoot infinite password reset loop issues in ServiceNow."
date: 2025-08-05
author: Shelby Evans
email: shelbyevans110@gmail.com
labels:
  - password
  - reset
  - loop
  published: true
---

## symptoms

- User clicks "Reset Password" and is immediately prompted again.
- No password reset email arrives in the inbox.
- Multiple reset requests flood the mail queue

## Root Cause

In this scenario, the password reset token TTL was set to 5 minutes, causing expired tokens to reject the reset and recycle the user back to the login page.

## Resolution Steps

1. Navigate to **System Properties → Security**  
2. Change **Password Reset Token Timeout** from 5 to 30 minutes  
3. Click **Save**  
4. Clear the ServiceNow cache (`System Clear → Cache`)

## Verification

1. Request a new password reset link. 
2. Click the link within 30 minutes. 
3. Confirm you reach the password reset form instead of the login page.

## Related Articles

- [Password Policy Configuration](./password-policy.md)
- [Email Workflow Troubleshooting](./email-workflow.md)


