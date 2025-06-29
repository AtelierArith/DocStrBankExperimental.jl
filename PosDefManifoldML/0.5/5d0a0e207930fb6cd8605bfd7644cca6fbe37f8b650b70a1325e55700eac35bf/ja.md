```julia
function crval(model    :: MLmodel,
               𝐏        :: ℍVector,
               y        :: IntVector;
        pipeline    :: Union{Pipeline, Nothing} = nothing,
        nFolds      :: Int     = min(10, length(y)÷3),
        shuffle     :: Bool    = false,
        scoring     :: Symbol  = :b,
        hypTest     :: Union{Symbol, Nothing} = :Bayle,
        verbose     :: Bool    = true,
        outModels   :: Bool    = false,
        ⏩           :: Bool    = true,
        fitArgs...)
```

機械学習 `model` に対する層別交差検証精度は、*k* 個のエルミート行列を保持する ℍVector $𝐏$ と、これらの行列に対する *k* のラベルを保持する [IntVector](@ref) `y` に基づいています。 [`CVres`](@ref) 構造体を返します。

各フォールドごとに、機械学習モデルがトレーニングデータにフィットし、テストデータに対してラベルが予測されます。出力構造体には、分類パフォーマンスの統計が保存されます。

**オプションのキーワード引数**

`pipeline` が提供されている場合、[`Pipeline`](@ref) 型で、パイプラインはトレーニングデータにフィットし、テストデータの予測に適用されます。

`nFolds` はデフォルトで 10 と観測数 ÷ 3（整数除算）の最小値に設定されます。

`scoring`=:b（デフォルト）の場合、**バランス精度**が計算されます。他の値を指定すると、関数は通常の**精度**を返します。バランス精度は不均衡なクラスに対して好まれます。バランスの取れたクラスの場合、バランス精度は通常の精度に減少するため、クラスがバランスしている場合は、通常の精度を使用する意味はありません。

!!! info "エラー損失"
    この関数は、各フォールドのエラー損失を計算することに注意してください（[`CVres`](@ref) を参照）。平均エラー損失は精度の補数であり、バランス精度の補数ではありません。クラスがバランスしている場合、`scoring`=:a（精度）を使用すると、各フォールド内の平均エラー損失は 1 から平均精度を引いたものに等しくなりますが、これはこの関数によっても計算されます。しかし、クラスが不均衡で `scoring`=:b（デフォルト）を使用する場合、返されるエラー損失と精度は一貫性がないように見えるかもしれません。


`hypTest` は `nothing` または実施される統計テストの種類を指定するシンボルです。現時点では、`：Bayle` のみが可能なシンボルであり、このテストはデフォルトで実行されます。ベイリーの手続きは、観測された平均バイナリエラー損失がランダムな偶然の仮説によって期待されるものよりも小さいかどうかをテストします。これは $1-\frac{1}{z}$ に設定され、$z$ はクラスの数です（[`testCV`](@ref) を参照）。

`shuffle` 引数の意味（デフォルトは false）については、内部的にこの引数が渡される関数 [`cvSetup`](@ref) を参照してください。

`seed` 引数の意味（デフォルトは 1234）については、内部的にこの引数が渡される関数 [`cvSetup`](@ref) を参照してください。

`verbose` が true（デフォルト）の場合、情報が REPL に出力されます。

`outModels` が true の場合、[`CVres`](@ref) 構造体と各フォールドにフィットしたモデルの `nFolds` ベクトルを保持する 2 タプルを返します。そうでない場合（デフォルト）、[`CVres`](@ref) 構造体のみを返します。

`⏩` の場合、計算はフォールド間でマルチスレッドで実行されます。デフォルトでは true です。この関数を実行する際に問題がある場合やデバッグのために false に設定してください。

!!! note "マルチスレッド"
    各フォールドに対して独立したスレッドで交差検証を実行する場合、`⏩=true`（デフォルト）を設定すると、各フォールド内で呼び出される [`fit!`](@ref) および [`predict`](@ref) 関数はシングルスレッドモードで実行されます。逆に、`⏩=false` を渡すと、これらの 2 つの関数はマルチスレッドモードで実行されます。これは、アクティブにするスレッドの数を超えないようにするために行われます。


`fitArgs` は、交差検証の各フォールドに対して呼び出される [`fit`](@ref) 関数に渡されるオプションのキーワード引数です。各機械学習モデルに対して、フィットメソッドのすべてのオプションのキーワード引数がここに渡すことができますが、以下の表にリストされている引数は渡さないでください。渡された場合、それらは無効になります：

|  MDM/MDMF  |    ENLR    |    SVM     |
|:----------:|:----------:|:----------:|
| `verbose`  | `verbose`  | `verbose`  |
|    `⏩`     |    `⏩`     |    `⏩`     |
| `meanInit` | `meanInit` | `meanInit` |
| `meanISR`  | `fitType`  |            |
|            | `offsets`  |            |
|            |  `lambda`  |            |
|            |  `folds`   |            |

`meanISR` 引数を渡す場合、これは何も指定しない（デフォルト）か I（単位行列）でなければなりません。接線空間モデルに対して `meanISR=I` を渡すと、点を接線空間に投影する前に単位行列に平行移動することは行われません。これは、`pipeline` に再中心化条件が渡される場合に使用できます（ENLR および SVM モデルの [`fit`](@ref) メソッドを参照）。

また、`w` 引数（重心推定のための重み）を渡す場合、重みのベクトルを渡さず、シンボルを渡してください。例えば、バランス重みのために `w=:b` を渡します。

**参照**: [記法と命名法](@ref)、[ℍVector 型](@ref)

**関連**: [`fit`](@ref)、[`predict`](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

# データを生成
P, _dummyP, y, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.2)

# 最小距離平均分類器を使用して 10 フォールド交差検証を実行
cv = crval(MDM(Fisher), P, y)

# 前処理パイプラインを適用して同じことを行う
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
cv = crval(MDM(Fisher), P, y; pipeline = p)

# 前処理パイプラインを適用し、データを I の接線空間に投影
# 行列を再中心化せずに行います。
# これは接線空間 ML モデルに対してのみ意味があります。
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)
cv = crval(ENLR(Fisher), P, y; pipeline = p, meanISR=I)

# ラッソロジスティック回帰分類器を使用して 10 フォールド交差検証を実行
cv = crval(ENLR(Fisher), P, y)

# ...サポートベクターマシン分類器を使用して
cv = crval(SVM(Fisher), P, y)

# ...次数 3 の多項式カーネルを使用して（デフォルト）
cv = crval(SVM(Fisher), P, y; kernel=kernel.Polynomial)

# 代わりに 8 フォールド交差検証を実行
# （PC に 8 スレッドがある場合はかなり速く実行できることに注意）
cv = crval(SVM(Fisher), P, y; nFolds=8)

# ...接線空間投影のために重みをバランスさせる
cv = crval(ENLR(Fisher), P, y; nFolds=8, w=:b)

# フォールドをシャッフルして別の交差検証を実行
cv = crval(ENLR(Fisher), P, y; shuffle=true, nFolds=8, w=:b)

```
