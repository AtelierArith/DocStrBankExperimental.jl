```julia
create_3d_model(
    agents::Array{EasyABM.Agent3D{S<:Union{Float64, Int64}, A<:EasyABM.SType, B<:EasyABM.MType}, 1};
    graphics,
    agents_type,
    size,
    random_positions,
    space_type,
    kwargs...
) -> Union{EasyABM.SpaceModel3D{EasyABM.StaticType, S, EasyABM.PeriodicType} where S<:Float64, EasyABM.SpaceModel3D{EasyABM.StaticType, S, EasyABM.PeriodicType} where S<:Int64}

```

Creates a 3d model with 

  * `agents` : list of agents.
  * `graphics` : if true, properties of shape, color, orientation will be assigned to each agent by default, if not already assigned by the user.
  * `agents_type` : Set it to Static if number of agents is fixed during model run. Otherwise set it to Mortal.
  * `size` : A tuple (dimx, dimy, dimz) which tells the number of blocks the space is to be divided into along x, y and z directions. An agent can take

positions from 0 to dimx in x-direction, 0 to dimy in y direction and 0 to dimz in z direction. The agents can move continuously or  in discrete steps depending upon how user implements the step rule (unless the agents are of grid type which can only move in dicrete steps).  Each unit block of space is called a patch which like agents can be assigned  its own properties.  

  * `random_positions` : If this property is true, each agent, will be assigned a random position.
  * `space_type` : Set it to Periodic or NPeriodic depending upon if the space is periodic or not.
  * `kwargs`` : Keyword argments used as model properties.
