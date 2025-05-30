```
@tasks for ... end
```

並列で実行できるタスクのセットを生成することで、`for` ループを並列化するためのマクロです。タスクをいくつ生成するか、イテレーション空間をタスク間でどのように分配するか（その他の設定も含む）は、ループ本体の `@set` ステートメントを通じて構成できます。

還元（`@set reducer=<reducer function>`）と結果の収集（`@set collect=true`）をサポートしています。

内部的には、`for` ループは対応する並列 [`tforeach`](@ref)、[`tmapreduce`](@ref)、または [`tmap`](@ref) 呼び出しに変換されます。

関連情報: [`@set`](@ref)、[`@local`](@ref)

## 例

```julia
using OhMyThreads: @tasks
```

```julia
@tasks for i in 1:3
    println(i)
end
```

```julia
@tasks for x in rand(10)
    @set reducer=+
    sin(x)
end
```

```julia
@tasks for i in 1:5
    @set collect=true
    i^2
end
```

```julia
@tasks for i in 1:100
    @set ntasks=4*nthreads()
    # 非均一な作業...
end
```

```julia
@tasks for i in 1:5
    @set scheduler=:static
    println("i=", i, " → ", threadid())
end
```

```julia
@tasks for i in 1:100
    @set begin
        scheduler=:static
        chunksize=10
    end
    println("i=", i, " → ", threadid())
end
```
