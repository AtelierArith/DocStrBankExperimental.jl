```
AbstractState_build_phase_envelope(handle::Clong, level::AbstractString)
```

Build the phase envelope.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `level`: How much refining of the phase envelope ("none" to skip refining (recommended) or "veryfine")

# Note

If there is an error in an update call for one of the inputs, no change in the output array will be made

# Ref

CoolPRop::AbstractState*build*phase*envelope(const long handle, const char* level, long* errcode, char* message*buffer, const long buffer_length);
