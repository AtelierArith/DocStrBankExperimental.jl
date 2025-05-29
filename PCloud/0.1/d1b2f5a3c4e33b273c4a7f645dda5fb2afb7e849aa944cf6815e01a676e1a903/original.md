```
pcloud_diff(client::PCloudClient; kwargs...)
```

List updates of the user's folders/files.

Optionally, takes the parameter `diffid`, which if provided returns only changes since that `diffid`.

Alternatively you can provide date/time in `after` parameter and you will only receive events generated after that time.

Another alternative to providing `diffid` or `after` is providing `last`, which will return `last` number of events with highest diffids (that is the last events).

Especially setting `last` to 0 is optimized to do nothing more than return the last `diffid`.

If the optional parameter `block` is set and there are no changes since the provided `diffid`, the connection will block until an event arrives. Blocking only works when `diffid` is provided and does not work with either `after` or `last`.

However, sending any additional data on the blocked connection will unblock the request and an empty set will be returned. This is useful when you want to monitor for updates when idle and use connection for other activities when needed.

Just keep in mind that if you send any request on a connection that is blocked, you will receive two replies - one with empty set of updates and one answering your second request.

If the optional `limit` parameter is provided, no more than `limit` entries will be returned.

*IMPORTANT* When a folder/file is created/delete/moved in or out of a folder, you are supposed to update modification time of the parent folder to the timestamp of the event.

*IMPORTANT* If your state is more than 6 months old, you are advised to re-download all your state again, as we reserve the right to compact data that is more than 6 months old.

Compacting means that if a deletefolder/deletefile event is more than 6 month old, it will disappear altogether with all create/modify events. Also, if modifyfile is more than 6 months old, it can become createfile and the original createfile will disappear. That is not comprehensive list of compacting activities, so you should generally re-download from zero rather than trying to cope with compacting.

Source: https://docs.pcloud.com/methods/general/diff.html

# Optional Arguments

  * `diffid::Int`: receive only changes since that diffid.
  * `after::datetime`: receive only events generated after that time
  * `last::Int`: return last number of events with highest diffids (that is the last events)
  * `block::Int`: if set, the connection will block until an event arrives. Works only with diffid
  * `limit::Int`: if provided, no more than limit entries will be returned

# Output

On success in the reply there will be `entries` array of objects and `diffid`. Set your current `diffid` to the provided `diffid` after you process all events, during processing set your state to the `diffid` of the event preferably in a single transaction with the event itself.

Each object will have at least:

  * `diffid::Int`: the event's identificator
  * `time::datetime`: timestamp of the event
  * `event::event`: see the possible events here

In most cases also metadata will be provided.

`diffid` could be used to request updates since this event. Normally diffids are incrementing integers, but one can not assume that ids are consecutive as events that cancel each other (e.g. createfolder, deletefolder) are not displayed if they happen to be in the same list.

For shares, a share object is provided.

`time` of the event is the time of the event - even if the event is createfolder, `time` is not guaranteed to be the folder's creation time. The folder might be somebody elses folder,created an year ago, that was just shared with you.
