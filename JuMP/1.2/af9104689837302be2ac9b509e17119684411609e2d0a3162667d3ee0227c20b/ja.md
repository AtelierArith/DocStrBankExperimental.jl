```
@constraint(m::Model, expr, kw_args...)
```

式 `expr` で説明される制約を追加します。

```
@constraint(m::Model, ref[i=..., j=..., ...], expr, kw_args...)
```

式 `expr` によってパラメータ化された制約のグループを追加します。

式 `expr` は次のいずれかの形式を取ることができます。

  * `func in set` の形式で、関数 `func` が `set` に属することを制約します。`set` は [`MOI.AbstractSet`](https://jump.dev/MathOptInterface.jl/v0.6.2/apireference.html#Sets-1) であるか、JuMP のショートカットのいずれか [`SecondOrderCone`](@ref)、[`RotatedSecondOrderCone`](@ref)、[`PSDCone`](@ref) です。例えば、`@constraint(model, [1, x-1, y-2] in SecondOrderCone())` は `[x-1, y-2]` のノルムが 1 未満であることを制約します。
  * `a sign b` の形式で、`sign` は `==`、`≥`、`>=`、`≤`、`<=` のいずれかで、式 `a` と `b` の比較が成り立つように単一の制約を構築します。例えば、`@constraint(m, x^2 + y^2 == 1)` は `x` と `y` が単位円上にあることを制約します。
  * `a ≤ b ≤ c` または `a ≥ b ≥ c` の形式（`≤` と `<=`（それぞれ `≥` と `>=`）は互換的に使用できます）で、ペアの式 `b` が `a` と `c` の間にあることを制約します。
  * `@constraint(m, a .sign b)` または `@constraint(m, a .sign b .sign c)` の形式で、ベクトルの各要素に対して制約の作成をブロードキャストします。

`kw_args` で認識されるキーワード引数は次のとおりです。

  * `base_name`: 制約名を生成するために使用される名前のプレフィックスを設定します。スカラー制約の制約名に対応し、それ以外の場合、制約名は各軸 `axes` のインデックス `...` に対して `base_name[...]` に設定されます。
  * `container`: コンテナの型を指定します。
  * `set_string_name::Bool = true`: [`MOI.ConstraintName`](@ref) 属性を設定するかどうかを制御します。`set_string_name = false` を渡すことでパフォーマンスが向上する可能性があります。

## 制約マクロを拡張するための注意

各制約は `add_constraint(m, build_constraint(_error, func, set))` を使用して作成されます。

  * `_error` は、エラーメッセージを引数として与えるのに加えて、制約呼び出しを示すエラーファンクションです。
  * `func` は制約される式です。
  * `set` はそれが属するセットです。

最初のタイプの `expr`（すなわち `@constraint(m, func in set)`）の場合、`func` と `set` は変更されずに `build_constraint` に渡されますが、他のタイプの場合は、式と記号から決定されます。例えば、`@constraint(m, x^2 + y^2 == 1)` は `add_constraint(m, build_constraint(_error, x^2 + y^2, MOI.EqualTo(1.0)))` に変換されます。

この形式の新しい制約を受け入れるために JuMP を拡張するには、`build_constraint` に対応するメソッドを追加する必要があります。これは、`func` または `set` が `Symbol` などのカスタム型であることを意味する可能性が高いです。なぜなら、制約に現れる関数やセットの型に基づいてディスパッチしたいからです。

`func` と `set` だけでなく、より多くの情報を持つ制約を作成する必要がある拡張の場合、`@constraint` に追加の位置引数を指定でき、それが `build_constraint` に渡されます。したがって、`build_constraint(_error, func, set, my_arg; kw_args...)` の拡張を定義することで、この構文を有効にできます。これにより、ユーザー構文は次のようになります: `@constraint(model, ref[...], expr, my_arg, kw_args...)`。
