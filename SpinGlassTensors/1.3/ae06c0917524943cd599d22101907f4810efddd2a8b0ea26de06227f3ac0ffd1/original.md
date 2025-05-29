`PoolOfProjectors` is a data structure for managing projectors associated with Ising model sites. It allows efficient storage and retrieval of projectors based on their indices and provides support for different computational devices.

# Fields:

  * `data::Dict{Symbol, Dict{Int, Proj{T}}}`: A dictionary that stores projectors associated with different

computational devices (`:CPU`, `:GPU`, etc.). The inner dictionary maps site indices to projectors.

  * `default_device::Symbol`: A symbol representing the default computational device for projectors in the pool.
  * `sizes::Dict{Int, Int}`: A dictionary that maps site indices to the maximum projector size for each site.

# Constructors:

  * `PoolOfProjectors(data::Dict{Int, Dict{Int, Vector{T}}}) where T`: Create a `PoolOfProjectors` with initial data for projectors.

The data is provided as a dictionary that maps site indices to projectors stored in different computational devices. The `sizes` dictionary is automatically populated based on the maximum projector size for each site.

  * `PoolOfProjectors{T}() where T`: Create an empty `PoolOfProjectors` with no projectors initially stored.
