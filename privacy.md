# SBB Blueprints Privacy Notice

Effective date: September 9, 2026

SBB Blueprints is a Reddit-hosted Devvit app for publishing and discovering
Palworld blueprint posts. This notice describes the data used by the app. It
does not replace Reddit's own privacy policy or the privacy rules of the
community where the app is installed.

## Data the app uses

When a redditor publishes a blueprint, the app stores the following information
inside the Devvit Redis database assigned to that subreddit installation:

- Reddit post ID, author account ID, and author username;
- the title, description, game version, compatibility, status, required mods,
  tags, and Reddit-hosted preview-image URL supplied for the blueprint;
- the blueprint code and a one-way SHA-256 hash used to reject exact duplicate
  codes; and
- creation/update timestamps, internal metadata synchronization state, and an
  anonymous aggregate count of successful blueprint-code copies.

When **Copy Code** succeeds, the app increments only the copied blueprint's
aggregate counter. It does not store the reader's account ID or username, a
per-reader copy history, or an individual copy timestamp.

The app also uses short-lived operational records for rate limiting,
authorization caching, edit locking, and navigation. The app does not request
passwords, email addresses, real names, precise locations, private messages, or
external account credentials.

## How the data is used

The information is used only to create and render the blueprint post, let the
author or community moderators edit it, provide **My Blueprints**, copy the
blueprint code, synchronize searchable Reddit flair and fallback content, and
protect the service from duplicate or excessive submissions.

The preview image and public blueprint details appear on the Reddit post. The
full blueprint code is not placed in Reddit post data or text fallback, but it
is intentionally available to people who open the post and press **Copy Code**.
Do not submit a blueprint code that you intend to keep private.

## Storage and sharing

Blueprint metadata and codes remain within Reddit's Devvit infrastructure.
Preview images are uploaded to Reddit's media service. Each subreddit
installation has an isolated Redis database; the app has no external database,
HTTP-fetch integration, advertising tracker, data broker, or account-linking
service. The developer does not sell, license, or use this data to train an AI
model.

Reddit and the moderators of the community may process public posts under their
own terms, policies, and moderation practices.

## Retention and deletion

Blueprint data remains available while its Reddit post exists. When Reddit sends
the app a post-deletion event, the app removes the corresponding metadata, code,
duplicate-code ownership record, and discovery indexes from Redis. Reddit-hosted
image retention is controlled by Reddit.

Devvit Web does not currently expose an account-deletion trigger. To account for
this, an hourly bounded privacy sweep checks known blueprint posts and removes
the cached author account ID, username, and **My Blueprints** index entry after
Reddit marks the post author as deleted. Short-lived authorization and rate
limit records expire automatically.

## Choices and contact

Authors can update their blueprint through the post's **Edit** action. To remove
the app's copy of a blueprint, delete the corresponding Reddit post. Readers can
report a blueprint through Reddit's native post-report menu.

For privacy questions or deletion problems, contact `u/leafnwind` on Reddit or
send Modmail to the moderators of the community where the app is installed and
include the affected Reddit post link.

This notice may be updated when the app's data practices change. Material
changes will be reflected in the effective date above.
