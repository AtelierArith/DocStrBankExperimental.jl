`SigAction` is the counterpart of the C `struct sigaction` structure.  It is used to specify the action taken by a process on receipt of a signal.  Assuming `sa` is an instance of `SigAction`, its fields are:

```julia
sa.handler         # address of a signal handler
sa.mask            # mask of the signals to block
sa.flags           # bitwise flags
```

where `sa.handler` is the address of a C function (can be `SIG_IGN` or `SIG_DFL`) to be called on receipt of the signal.  This function may be given by `cfunction`.  If `IPC.SA_INFO` is not set in `sa.flags`, then the signature of the handler is:

```julia
function handler(signum::Cint)::Nothing
```

that is a function which takes a single argument of type `Cint` and returns nothing; if `IPC.SA_INFO` is not set in `sa.flags`, then the signature of the handler is:

```julia
function handler(signum::Cint, siginf::Ptr{SigInfo}, unused::Ptr{Cvoid})::Nothing
```

that is a function which takes 3 arguments of type `Cint`, `Ptr{SigInfo}`, `Ptr{Cvoid}` repectively and which returns nothing.  See [`SigInfo`](@ref) for a description of the `siginf` argument by the handler.

Call:

```julia
sa = SigAction()
```

to create a new empty structure or

```julia
sa = SigAction(handler, mask, flags)
```

to provide all fields.

See also [`SigInfo`](@ref), [`sigaction`](@ref) and [`sigaction!`](@ref).
