UserRiskrator
=============

Important note
--------------

This plugin is just a concept (at the moment). Do not use it in production.


The idea
--------

We'd like to identify user accounts with suspicious activity. This is with with
aim to identify and address:

 * possible compromised accounts,
 * users with alicious intent, and
 * attempts to bridge our application's security.

We aim to achieve this by monitoring user's activity accross time for multiple
requests. For example:

 * Failing to log into our application once might be a user simply
making a spelling mistake, failing to log in 20 times is very suspicious.
 * Requesting a non-existend application path once might be a silly mistake,
requesting 10 non-existend urls is very suspicious.
 * Generating an exception in our application is probably just a bug, generating
multiple exceptions is very suspicious.

*User Riskrator* aims to provide the visibility needed to identify suspicious
activity.


So, what do you get
-------------------

    >> user = User.first
    => #<User id: 1, login: "siebert", ... , remember_token_expires_at: nil>
    >> user.risk_rating
    => 13
    >> user.log_risky_event("FailedLoginAttempt")
    => true
    >> user.risky_events
    => [#<RiskyEvent id: 1, event: "Failed login attempt", risk_rating: 5, ...">]



Copyright (c) 2011 Siebert Lubbe, released under the MIT license
