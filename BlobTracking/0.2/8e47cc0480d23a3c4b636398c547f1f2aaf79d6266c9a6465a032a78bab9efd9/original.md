```
update!(ws::Workspace, bt::BlobTracker, coords_or_img, result::TrackingResult)
```

Perform one iteration of predict and correct

#Arguments:

  * `ws`: a Workspace object
  * `bt`: the blob tracker
  * `coords_or_img`: vector of coordinates or an image
  * `result`: a `TrackingResult`
