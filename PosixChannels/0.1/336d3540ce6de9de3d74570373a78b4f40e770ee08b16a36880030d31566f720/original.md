```
PosixChannel{T}(name, kwargs...)
```

Create a `PosixChannel` that works with messages of type `T`.

*Notes*: `T` must be a plain data type (`isbitstype` must return `true`), and the message queue must allow for messages of at least `sizeof(T)`.

# Extended help

# Arguments

See [`man 3 mq_open`](https://man7.org/linux/man-pages/man3/mq_open.3.html) for details.

## All usages

  * `mode::Symbol=:rw`: the opening mode of the POSIX queue, can be `:r`, `:w`, or `:rw`.
  * `cloexec::Bool=false`: Activate the `O_CLOEXEC` flag.
  * `create::Bool=true`: Activate the `O_CREAT` flag.
  * `excl::Bool=false`: Activate the `O_CREAT` flag.
  * `nonblock::Bool=false`: Activate the `O_NONBLOCK` flag.

## Creation specifics

When creating a new queue (flag `O_CREAT` activated), it is necessary to provide additional informations. 

  * `create_r_user::Bool=true`: Make queue readable for user.
  * `create_w_user::Bool=true`: Make queue writable for user.
  * `create_r_group::Bool=true`: Make queue readable for the group of the user.
  * `create_w_group::Bool=true`: Make queue writable for the group of the user.
  * `create_r_other::Bool=false`: Make queue readable for other users.
  * `create_w_other::Bool=false`: Make queue writable for other users.
  * `create_len::Int=systemmsgdefault()`: Maximum number of messages in the queue.
  * `create_msg_size::Int=sizeof(T)`: Maximum size of a message.

# Examples

Start two julia REPL (a sender and a receiver).

`sender.jl`:

```julia
using PosixChannels

chan = PosixChannel{Int}("posix_channels_are_fun", mode=:w)
print("Press [Enter] when you are ready to send data.")
readline()

for i in 1:10
    put!(chan, i)
end

println("Done!")
println("Closing the channel.")
close(chan)

```

`receiver.jl`

```julia
using PosixChannels

chan = PosixChannel{Int}("posix_channels_are_fun", mode=:r)
println("Listening for 10 incoming Int, you may start sending")

for _ in 1:10
    while !isready(chan)
        wait(chan)
    end
    msg = take!(chan)
    println("Received $msg")
end

println("Done!")
println("Closing the channel.")
close(chan)
println("Deleting the channel.")
unlink(chan)
```

You can then launch each script, and press return in the sender's window.

```bash
$ julia --project sender.jl
Press [Enter] when you are ready to send data.
Done!
Closing the channel.
```

```bash
$ julia --project receiver.jl
Listening for 10 incoming Int, you may start sending
Received 1
Received 2
Received 3
Received 4
Received 5
Received 6
Received 7
Received 8
Received 9
Received 10
Done!
Closing the channel.
Deleting the channel.
```

!!! note "Types of messages"
    This example uses integers, but any type that verifies `isbitstype` could be used. See [`StaticStrings`](https://github.com/mkitti/StaticStrings.jl) for example.


See also [`wait`](@ref), [`put!`](@ref), [`take!`](@ref), [`unlink`](@ref), [`isnonblocking`](@ref).
