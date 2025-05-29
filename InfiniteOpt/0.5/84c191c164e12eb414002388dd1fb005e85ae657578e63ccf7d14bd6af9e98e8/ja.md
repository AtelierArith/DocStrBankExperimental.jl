```
build_parameter_function(
    _error::Function, 
    func::Function, 
    parameter_refs::Union{GeneralVariableRef, AbstractArray{<:GeneralVariableRef}, Tuple}
    )::ParameterFunction
```

[`ParameterFunction`](@ref) オブジェクトを構築します。このオブジェクトは、無限のパラメータをインプットとして受け取るパラメータ関数 `func` を使用します。最終的には、非線形の無限パラメータの振る舞いを可能にしたり、無限のドメインにわたるデータを組み込むために式に組み込むことができます。

ここで `func` は次の形式である必要があります：

```
func(paramvals...)::Float64
```

`paramvals` のフォーマットはポイント変数に類似しており、`parameter_refs` で与えられた無限パラメータ参照のタプルに基づきます。

無限パラメータタプルのフォーマットが不正な場合はエラーが発生します。許可されるフォーマットは無限変数のそれに従います。また、関数が `parameter_refs` のサポート実現を入力として受け入れない場合もエラーが発生します。

**例**

```julia-repl
julia> f = build_parameter_function(error, sin, t);
```
