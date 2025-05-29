```julia
struct RA4Step <: SlottedRandomAccess.FixedRepSlottedRAScheme{1}
```

Type representing the 4-step RA procedure, where Slotted ALOHA is used during the RA contention period (msg1) and succesfully decoded msg1 packets are used to allocate orthogonal resources for the msg3 transmission of the actual data.

!!! note
    This type of RA scheme will only simulate the packet decoding process for the msg1 and optionally limit the maximum number of succesfull packets per frame to be the number of slots available for msg3 transmission.


# Fields

  * `msg1_occasions::Int64`: Number of time occasions (slots) in each RA frame allocated to the msg1 random access.
  * `msg3_occasions::Int64`: Number of time occasions (slots) in each RA frame allocated to the msg3 transmission.
  * `freq_slots::Int64`: Number of frequency slots (i.e. sub-carriers) available in each time slot, it is assumed that the number of subcarriers is the same for both msg1 and msg3 transmissions.
  * `limit_packets::Bool`: Flag to specify whether to limit the number of maximum decoded packet to the number of slots associated to msg3 transmission (which is equivalent to `msg3_occasions * freq_slots`).

# Constructors

```
RA4Step(msg1_occasions, msg3_occasions; freq_slots = 48, limit_packets = true)
```

## Example

The code below will generate a 4-step RA scheme with 5 time occasions for msg1 every 2 time occasions for msg3, while assuming 20 frequency slots (i.e. subcarriers) for each time slots and while limiting the maximum number of decoded packets in each frame to the actual number of msg3 slots (which is `2 * 20`).

```julia-repl
julia> scheme = RA4Step(5, 2; freq_slots = 20, limit_packets = true)
```

See also: [`CRDSA`](@ref), [`MF-CRDSA`](@ref)
