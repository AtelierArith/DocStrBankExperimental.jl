`SigInfo` represents a C `siginfo_t` structure.  It should be considered as opaque, its contents is stored as a tuple of unsigned integers whose size matches that of `siginfo_t` but, in principle, only a pointer of it should be received by a signal handler established with the `SA_SIGINFO` flag.

Given `ptr`, an instance of `Ptr{SigInfo}` received by a signal handler, the members of the corresponding C `siginfo_t` structure are retrieved by:

```julia
IPC.siginfo_signo(ptr)  # Signal number.
IPC.siginfo_code(ptr)   # Signal code.
IPC.siginfo_errno(ptr)  # If non-zero, an errno value associated with this
                        # signal.
IPC.siginfo_pid(ptr)    # Sending process ID.
IPC.siginfo_uid(ptr)    # Real user ID of sending process.
IPC.siginfo_addr(ptr)   # Address of faulting instruction.
IPC.siginfo_status(ptr) # Exit value or signal.
IPC.siginfo_band(ptr)   # Band event for SIGPOLL.
IPC.siginfo_value(ptr)  # Signal value.
```

These methods are *unsafe* because they directly use an address.  They are therefore not exported by default.  Depending on the context, not all members of `siginfo_t` are relevant (furthermore they may be defined as union and thus overlap in memory).  For now, only the members defined by the POSIX standard are accessible.  Finally, the value given by `IPC.siginfo_value(ptr)` represents a C type `union sigval` (an union of a C `int` and a C `void*`), in Julia it is returned (and set in [`sigqueue`](@ref)) as an integer large enough to represent both kind of values.
