```
@local name = value

@local name::T = value
```

は、明示的に型指定された代入を介して[タスクローカル値](@ref TLS) (TLV)を指定するために`@tasks for ... end`ブロック内で使用できます。これらの値はタスクごとに一度だけ割り当てられ（反復ごとではなく）、異なるタスクローカルの反復間で再利用できます。

`@tasks for ... end`ブロック内には単一の`@local`ブロックしか存在できません。複数のTLVを指定するには、`@local begin ... end`を使用します。ただし、通常の代入と比較していくつかの制限があります。たとえば、TLVは互いに参照できません。

## 例

```julia
using OhMyThreads: @tasks
using OhMyThreads.Tools: taskid

@tasks for i in 1:10
    @set begin
        scheduler=:dynamic
        ntasks=2
    end
    @local x = zeros(3) # TLV

    x .+= 1
    println(taskid(), " -> ", x)
end
```

```julia
@tasks for i in 1:10
    @local begin
        x = rand(Int, 3)
        M = rand(3, 3)
    end
    # ...
end
```

`@local`によって作成されたタスクローカル変数は、デフォルトで推論された型に制約されますが、必要に応じて宣言時に異なる型を指定することもできます：

```julia
@tasks for i in 1:10
    @local x::Vector{Float64} = some_hard_to_infer_setup_function()
    # ...
end
```

代入の右辺はループ本体の外に持ち上げられ、タスクローカル値を初期化するために使用されるクロージャとしてキャプチャされます。これは、クロージャのスコープがループのスコープではなく（見た目はそうですが）、むしろループ本体を囲むスコープであることを意味します。(`@macroexpand`は、`@tasks`ブロックの生成されたコードを検査するための便利なツールです。)
