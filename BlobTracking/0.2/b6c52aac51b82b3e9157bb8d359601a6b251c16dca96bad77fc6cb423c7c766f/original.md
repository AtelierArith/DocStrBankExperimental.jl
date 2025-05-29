```
track_blobs(bt::BlobTracker, vid; display=false, recorder=nothing, threads=Threads.nthreads() > 1, ignoreempty=false)
```

Main entry point to tracking blobs

#Arguments:

  * `bt`: a BlobTracker
  * `vid`: Some iterable thing that iterates images
  * `display = Base.display`: function to display images live. Displaying live slows things down a bit. Use `display=nothing` to not display anything. Consider also `c = imshow(img);

displayfun = img -> imshow!(c["gui"]["canvas"],img); `.

  * `recorder`: an optional `Recorder` that can record each frame to a video on disk. Recording things does not slow things down much and also does not affect memory usage much.
  * `threads`: Use threaded processing of frames? Only useful if Julia is started with multiple threads.
  * `ignoreempty=false`: wether or not to ignore display and recording of frames which contains no blobs and no measurements.
