Tracks an event

# Arguments

  * `analytics::Analytics`
  * `attrs::Dict`: Event payload

## Possible attrs

  * `event::String`: Event name
  * `properties::Dict`: Event properties (optional)
  * `anonymous_id::String`: ID for a user when you don't know who they are yet. (optional but you must provide either an `anonymous_id` or `user_id`)
  * `context::Dict`: (optional)
  * `integrations::Dict`:  What integrations this event goes to (optional)
  * `message_id::String`: ID that uniquely identifies a message across the API. (optional)
  * `timestamp::Union{DateTime, ZonedDateTime}`: When the event occurred (optional)
  * `user_id::String`: The ID for this user in your database (optional but you must provide either an `anonymous_id` or `user_id`)
  * `options::Dict`: Options such as user traits (optional)

# Example

```julia
using SegmentAnalytics

analytics = SegmentAnalytics.Analytics(write_key="write_key")
payload = Dict(
  :event => "Event Name",
  :user_id => "User ID",
  :properties => Dict(:p1 => 1, :p2 => 2),
  :message_id => "custom-message-id"
)

track(analytics, payload)
```
