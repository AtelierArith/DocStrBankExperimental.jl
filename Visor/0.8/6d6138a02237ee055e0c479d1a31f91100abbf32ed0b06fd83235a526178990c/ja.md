```
startup(supervisor::Supervisor, proc::Supervised)
```

`proc`で定義された監視プロセスを`supervisor`の子として開始します。

```jldoctest
julia> using Visor

julia> foo(self) = println("foo process started");

julia> main(self) = startup(self.supervisor, process(foo));

julia> supervise([process(main)]);
foo process started
```
