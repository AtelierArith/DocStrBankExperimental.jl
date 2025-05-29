```
PriorityChannel(func::Function; ctype=Any, csize=1, taskref=nothing)
```

`func`から新しいタスクを作成し、それを型`ctype`およびサイズ`csize`の新しいチャネルにバインドし、タスクをスケジュールします。すべてを1回の呼び出しで行います。

`func`は、バインドされたチャネルを唯一の引数として受け取る必要があります。

作成されたタスクへの参照が必要な場合は、キーワード引数`taskref`を介して`Ref{Task}`オブジェクトを渡してください。

`PriorityChannel`を返します。

# 例

```jldoctest
julia> chnl = PriorityChannel(c->foreach(i->put!(c,i), 1:4));

julia> typeof(chnl)
PriorityChannel{Any,Int64}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

作成されたタスクを参照する:

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = PriorityChannel(c->(@show take!(c)); taskref=taskref);

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
take!(c) = "Hello"

julia> istaskdone(taskref[])
true
```
