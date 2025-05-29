```
InteractionTransformer
```

相互作用トランスフォーマーを構築するためのモデルタイプで、[MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにタイプをインポートできます。

```
InteractionTransformer = @load InteractionTransformer pkg=MLJModels
```

`model = InteractionTransformer()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`InteractionTransformer(order=...)`のようにキーワード引数を提供します。

選択した列のサブセットに対して、指定された次数までのすべての多項式相互作用項を生成します。要素にscitype `<:Infinite`を含む列は、相互作用を生成するための有効な基底です。`features`が指定されていない場合、テーブル内のscitype `<:Infinite`を持つすべての列が基底として使用されます。

MLJまたはMLJBaseでは、次の単一の呼び出しで特徴`X`を変換できます。

```
transform(machine(model), X)
```

以下の例も参照してください。

# ハイパーパラメータ

  * `order`: 生成される相互作用の最大次数。
  * `features`: 相互作用生成を制限する列。

# 操作

  * `transform(machine(model), X)`: 指定されたハイパーパラメータを使用して、テーブル`X`から多項式相互作用項を生成します。

# 例

```
using MLJ

X = (
    A = [1, 2, 3],
    B = [4, 5, 6],
    C = [7, 8, 9],
    D = ["x₁", "x₂", "x₃"]
)
it = InteractionTransformer(order=3)
mach = machine(it)

julia> transform(mach, X)
(A = [1, 2, 3],
 B = [4, 5, 6],
 C = [7, 8, 9],
 D = ["x₁", "x₂", "x₃"],
 A_B = [4, 10, 18],
 A_C = [7, 16, 27],
 B_C = [28, 40, 54],
 A_B_C = [28, 80, 162],)

it = InteractionTransformer(order=2, features=[:A, :B])
mach = machine(it)

julia> transform(mach, X)
(A = [1, 2, 3],
 B = [4, 5, 6],
 C = [7, 8, 9],
 D = ["x₁", "x₂", "x₃"],
 A_B = [4, 10, 18],)

```
