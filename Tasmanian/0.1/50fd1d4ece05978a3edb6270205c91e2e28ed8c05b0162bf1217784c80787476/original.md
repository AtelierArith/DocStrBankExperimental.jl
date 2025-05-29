```
isAccelerationAvailable(tsg::TasmanianSG, acceleration_type)
```

returns true if the library has been compiled with support for acceleration_type. Even if this returns false, you can use the type for enableAcceleration, but the library will default to the next available type (see the Manual)
