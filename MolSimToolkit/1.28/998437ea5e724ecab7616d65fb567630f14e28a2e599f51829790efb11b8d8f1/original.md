```
Simulation(pdb_file::String, trajectory_file::String; frames=[1,2,3,5])
Simulation(pdb_file::String, trajectory_file::String; frames=9:2:20)
Simulation(pdb_file::String, trajectory_file::String; first=1, last=nothing, step=1)
Simulation(atoms::AbstractVector{<:AtomType}, trajectory_file::String; first=1, last=nothing, step=1)
```

Creates a new `Simulation` object. 

The first constructor creates a `Simulation` object from a PDB or mmCIF file and a trajectory file. It will use the `PDBTools.Atom` for the atom type, which will populate the `atoms` vector of the `Simulation` object. Currently, other atom types are supported, if the `MolSimToolkit.atomic_mass(::AtomType)` function is defined for the atom type.

With the second constructor, the `atoms` vector is passed as an argument. This is useful when the atoms are provided by a different source than the PDB file. 

The `frames` or `first`, `last`, and `step` arguments can be used to specify the frames to be iterated over:

```
- `frames` can be a vector of frame indices, e. g., `frames=[1,2,3,5]` or `frames=9:2:20`.
- `first`, `last`, and `step` are Integers that specify the frames to be iterated over. 
  If `last` is not specified, the last frame in the trajectory will be used.
```

A `Simulation` object contains a trajectory file and a PDB data of the atoms. It can be iterated over to obtain the frames in the trajectory. The `Simulation` object is a mutable struct that contains the following data, that can be retrieved by the corresponding functions:

  * `frame_range(::Simulation)`: the list of frames to be iterated over
  * `frame_index(::Simulation)`: the index of the current frame in the trajectory
  * `length(::Simulation)`: the number of frames to be iterated over in the trajectory file, considering the current range
  * `raw_length(::Simulation)`: the number of frames in the trajectory file
  * `atoms(::Simulation)`: the atoms in the simulation

The Simulation object can also be manipulated by the following functions:

  * `close(::Simulation)`: closes the trajectory file
  * `restart!(::Simulation)`: restarts the iteration over the trajectory file
  * `first_frame!(::Simulation)`: restarts the iteration over the trajectory file and places the current frame at the first frame in the trajectory
  * `current_frame(::Simulation)`: returns the current frame in the trajectory
  * `next_frame!(::Simulation)`: reads the next frame in the trajectory file and returns it. Moves the current frame to the next one.
  * `set_frame_range!(::Simulation; first, last, step)`: resets the range of frames to be iterated over.
  * `get_frame(::Simulation, iframe)`: returns the frame at the given index in the trajectory.

One important feature of the `Simulation` object is that it can be iterated over, frame by frame. 

The `pairs` iterator can also be used to iterate over the frames, returning a tuple with the frame index and the frame itself. 

The `enumerate` iterator can also be used to iterate over the frames, returning a tuple with the frame counter and the frame itself.

# Examples

```julia-repl # to be doctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(
           Testing.namd_pdb, Testing.namd_traj; 
           first = 2, step = 2, last = 4,
           # or frames = [2,4]
       );

julia> for frame in simulation 
           @show frame_index(simulation)
           # show x coordinate of first atom 
           @show positions(frame)[1].x
       end
frame_index(simulation) = 2
((positions(frame))[1]).x = 5.912472724914551
frame_index(simulation) = 4
((positions(frame))[1]).x = 7.346549034118652

julia> for (i, frame) in pairs(simulation)
           @show i, frame_index(simulation)
       end
(i, frame_index(simulation)) = (2, 2)
(i, frame_index(simulation)) = (4, 4)  

julia> for (i, frame) in enumerate(simulation)
           @show i, frame_index(simulation)
       end
(i, frame_index(simulation)) = (1, 2)
(i, frame_index(simulation)) = (2, 4)

```
