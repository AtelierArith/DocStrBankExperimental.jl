Get camera distortion parameters

Args:     camera*name (str) Name of the camera, for backwards compatibility, ID numbers such as 0,1,etc. can also be used     vehicle*name (str, optional) Vehicle which the camera is associated with     external (bool, optional) Whether the camera is an External Camera

Returns:     List (float) List of distortion parameter values corresponding to K1, K2, K3, P1, P2 respectively.
