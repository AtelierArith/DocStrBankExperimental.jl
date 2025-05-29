```julia
struct MF_CRDSA{N, F} <: SlottedRandomAccess.FixedRepSlottedRAScheme{N}
```

Type representing the *Multi-Frequency Contention Resolution Diversity Slotted ALOHA* (MF-CRDSA) scheme, with a number of replicas `N`.

This RA scheme was introduced in [this 2017 IEEE paper](https://doi.org/10.1109/TCOMM.2017.2696952).

The scheme can support a number of time slots that is different than the number of replicas, though the originating paper only implements a scheme where one replica (and only one) is sent in each time slot.

!!! note
    When specifying the number of frame slots in the [`PLR_SimulationParameters`](@ref), the total number of slots in the frame (`nslots`) is assumed to be the product of time slots and frequency slots.

    So for example when putting `nslots = 100` in the [`PLR_SimulationParameters`](@ref) and using a MF-CRDSA scheme with `time_slots = 2`, the number of frequency slots is assumed to be `50`.


The assumed number of time slots and the function used to generate them randomly can be modified through the structure fields listed below.

# Fields

  * `n_time_slots::Int64`: The number of time slots in each RA frame for this MF-CRDSA scheme, must be a number equal or greater than the number of replicas `N`
  * `time_slots_function::Any`: This function is used to generate the time slots (between 1 and `time_slots`). It should be a function (or callable) that takes no argument and return an `NTuple{N, Int}` with the time slots of each replica (without repetitions).

!!! note
    The current implementation still assumes that there is only a single replica per time slot, so while the `time_slots_function` is arbitrary, potentially wrong results will be returned if this is not the case.


# Constructors

```
MF_CRDSA{N}()
```

Default construct, which assumes `N` time slots (so one per replica) and that one replica is sent in each time slot (randomizing over the frequency slots).

```
MF_CRDSA{N}(n_time_slots::Int, time_slots_function)
```

More advanced constructor for the MF-CRDSA scheme, which allows specifying a number of time slots different than the number of replicas and the function to be used to generate randomly the time slots to use for each user in each frame.

## Example

The code below will generate a MF-CRDSA scheme with 2 replicas and 3 time slots, where the first time slot is always used for the first replica, while the second replica is sent randomly either in the 2nd or 3rd slot.

```julia-repl
julia> scheme = MF_CRDSA{2}(3, () -> (1, rand(2:3)))
```

See also: [`CRDSA`](@ref)
