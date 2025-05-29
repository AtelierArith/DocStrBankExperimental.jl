```
on(f, c::Camera, observables::Observable...)
```

When mapping over observables for the camera, we store them in the `steering_node` vector, to make it easier to disconnect the camera steering signals later!
