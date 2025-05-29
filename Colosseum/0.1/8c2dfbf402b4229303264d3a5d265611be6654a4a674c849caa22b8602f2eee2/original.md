Set camera distortion parameters

Args:     camera*name (str) Name of the camera, for backwards compatibility, ID numbers such as 0,1,etc. can also be used     distortion*params (dict) Dictionary of distortion param names and corresponding values                                 {"K1": 0.0, "K2": 0.0, "K3": 0.0, "P1": 0.0, "P2": 0.0}     vehicle_name (str, optional) Vehicle which the camera is associated with     external (bool, optional) Whether the camera is an External Camera
