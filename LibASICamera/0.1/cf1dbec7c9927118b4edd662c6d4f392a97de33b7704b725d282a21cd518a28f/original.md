```
open_camera(id::Integer)
```

Opens the ASI camera connection.

Open the camera before any interaction with the camera, this will not affect the camera which is capturing. Then you must call init_camera() to perform any actions.

# Args:

```
id: Camera ID
```

# Throws:

```
ASIError
```
