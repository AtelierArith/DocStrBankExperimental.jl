```
threadcall_apriltag_detector_detect(tag_detector, image)
```

*Experimental* call apriltag*detector*detect in a seperate thread using the experimantal `@threadcall` Detect tags from an image and return an array of apriltag*detection*t*. You can use apriltag*detections*destroy to free the array and the detections it contains, or call detection*destroy and zarray*destroy yourself.
