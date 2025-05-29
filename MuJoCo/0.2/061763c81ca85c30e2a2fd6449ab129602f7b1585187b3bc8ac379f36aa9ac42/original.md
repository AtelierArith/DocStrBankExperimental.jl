```
resetkey!(m::Model, d::Data, [keyframe = 1])
```

Resets the data struct to values in the supplied keyframe. 

If no keyframe is specified, the first keyframe is used. The keyframe is a 1-based index into the list supplied by the model's specification.
