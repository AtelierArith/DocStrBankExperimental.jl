```
ConditionContext{Values<:Union{NamedTuple,AbstractDict},Ctx<:AbstractContext}
```

条件付けに使用される値を含むモデルコンテキスト。値は、シンボルを値にマッピングするNamedTuple（例：`(a=1, b=2)`）または、変数名を値にマッピングするAbstractDict（例：`Dict(@varname(a) => 1, @varname(b) => 2)`）のいずれかです。前者はパフォーマンスが高いですが、後者はシンボルとして表現できない変数名がある場合に使用する必要があります。例えば、`@varname(x[1])`のように。
