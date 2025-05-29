```
@aagent [OptionalBasetype=FreeAgent] [OptionalSupertype=AbstractAlgebraicAgent] struct my_agent
    extra_fields...
end
```

カスタムエージェントタイプを定義し、デフォルトのインターフェースメソッドによって期待されるフィールドを含めます（[`FreeAgent`](@ref)を参照）。

フィールドはデフォルトで可変ですが、`const`キーワードを使用して不変として宣言することができます。

エージェントの名前を入力として受け取り、共通フィールドを埋めるコンストラクタを提供します。

# 例

```julia
@aagent struct Molecule
    age::Float64
    birth_time::Float64
    sales::Float64
end
```

オプションの基底型：

```julia
@aagent FreeAgent struct Molecule
    age::Float64
    birth_time::Float64
    sales::Float64
end
```

オプションの基底型とスーパタイプ：

```julia
@aagent FreeAgent AbstractMolecule struct Molecule
    age::Float64
    birth_time::Float64
    sales::Float64
end
```

パラメトリック型：

```julia
@aagent struct MyAgent{T <: Real, P <: Real}
    field1::T
    field2::P
end

MyAgent{Float64, Int}("myagent", 1, 2)
```
