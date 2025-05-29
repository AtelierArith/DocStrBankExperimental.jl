Spawned selected object in the world

Args:     object*name (str) Desired name of new object     asset*name (str) Name of asset(mesh) in the project database     pose (airsim.Pose) Desired pose of object     scale (airsim.Vector3r) Desired scale of object     physics*enabled (bool, optional) Whether to enable physics for the object     is*blueprint (bool, optional) Whether to spawn a blueprint || an actor

Returns:     str: Name of spawned object, in case it had to be modified
