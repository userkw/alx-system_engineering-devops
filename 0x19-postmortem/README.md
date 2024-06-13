My First Postmortem
Issue Summary
Duration of the outage:

Start: June 14, 2024, 14:30
End: June 14, 2024, 16:00
Impact:

The login system was down.
Users could not log in, affecting about 45% of our users.
Many users contacted support and complained on social media.
Root Cause:

A mistake in the DNS settings for the OAuth server.
Timeline
14:30: Monitoring alert showed many login failures.
14:32: On-call engineer started looking into the issue.
14:35: Thought the database had a problem.
14:45: Checked the database, but it was fine. Looked at the OAuth server next.
15:00: Thought it might be a network issue, but it wasn’t.
15:15: Asked the infrastructure team to check DNS settings.
15:30: Found the DNS mistake in the OAuth server.
15:45: Fixed the DNS settings.
16:00: Service was back to normal, users could log in again.
Root Cause and Resolution
Root Cause:

The DNS settings for the OAuth server were changed by mistake during an update. This made the server unreachable, so users could not log in.
Resolution:

Reverted the DNS settings to the correct ones. This fixed the issue and users could log in again.
Corrective and Preventative Measures
Improvements/Fixes:

Review DNS changes better:

Have more checks before changing DNS settings.
Require approval from more people before applying changes.
Better monitoring:

Add monitoring for DNS settings to catch mistakes quickly.
Improve alerts to tell the difference between login service and database problems.
Task List:

 Patch the login server to handle DNS issues better.
 Add monitoring for DNS settings and alerts.
 Update the process for changing DNS settings to include more reviews.
 Train the team on the new DNS change process.
 Create automated tests for DNS settings to catch errors before they go live.
