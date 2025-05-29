Add mesh name to detect in wild card format

For example: simAddDetectionFilterMeshName("Car**") will detect all instance named "Car**"

Args:     camera*name (str) Name of the camera, for backwards compatibility, ID numbers such as 0,1,etc. can also be used     image*type (ImageType) Type of image required     mesh*name (str) mesh name in wild card format     vehicle*name (str, optional) Vehicle which the camera is associated with     external (bool, optional) Whether the camera is an External Camera
