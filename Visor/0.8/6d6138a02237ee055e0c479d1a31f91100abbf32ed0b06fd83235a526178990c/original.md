```
startup(supervisor::Supervisor, proc::Supervised)
```

Start the supervised process defined by `proc` as child of `supervisor`.

```jldoctest
julia> using Visor

julia> foo(self) = println("foo process started");

julia> main(self) = startup(self.supervisor, process(foo));

julia> supervise([process(main)]);
foo process started
```
