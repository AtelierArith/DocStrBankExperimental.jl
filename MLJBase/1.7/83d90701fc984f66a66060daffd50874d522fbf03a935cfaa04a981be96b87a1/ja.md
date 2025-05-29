```
machine(model, args...; cache=true, scitype_check_level=1)
```

`model`をバインドし、いくつかの機械学習アルゴリズムのハイパーパラメータをデータ`args`に保存する`Machine`オブジェクトを構築します。`Machine`インスタンス`mach`で[`fit!`](@ref)を呼び出すと、アルゴリズムの適用結果が`mach`に保存され、`fitted_params(mach)`（学習したパラメータ）や`report(mach)`（その他の結果）を使用して検査できます。これにより、`predict`や`transform`などの操作を使用して新しいデータへの一般化が可能になります。

```julia
using MLJModels
X, y = make_regression()

PCA = @load PCA pkg=MultivariateStats
model = PCA()
mach = machine(model, X)
fit!(mach, rows=1:50)
transform(mach, selectrows(X, 51:100)) # または transform(mach, rows=51:100)

DecisionTreeRegressor = @load DecisionTreeRegressor pkg=DecisionTree
model = DecisionTreeRegressor()
mach = machine(model, X, y)
fit!(mach, rows=1:50)
predict(mach, selectrows(X, 51:100)) # または predict(mach, rows=51:100)
```

`cache=false`を指定すると、速度よりもメモリ管理が優先されます。

学習ネットワークを構築する際には、`Node`オブジェクトを具体的なデータの代わりに使用できますが、型や次元のチェックは適用されません。

### トレーニングデータの型に関するチェック

モデルは、[`scitype`](@ref)関数を使用してデータ要件を明示します。つまり、`typeof`関数の代わりに[`scitype`](@ref)関数を使用します。

`scitype_check_level > 0`の場合、`args`内の各`arg`のscitypeが計算され、これはモデルが期待するscitypeと比較されます。ただし、`args`に`Unknown` scitypesが含まれ、`scitype_check_level < 4`の場合は、これ以上のアクションは行われません。警告が発行されるかエラーがスローされるかはレベルによります。詳細については、デフォルトレベルを検査または変更するためのメソッド[`default_scitype_check_level`](@ref)を参照してください（起動時は`1`）。

### モデルプレースホルダーを持つマシン

シンボルは、トレーニング時に指定されたモデルのプレースホルダーとして機械コンストラクタ内でモデルの代わりに使用できます。シンボルは、対応する値がモデルである構造体のフィールド名でなければなりません。以下の例に示すように：

```julia
mutable struct MyComposite
    transformer
    classifier
end

my_composite = MyComposite(Standardizer(), ConstantClassifier)

X, y = make_blobs()
mach = machine(:classifier, X, y)
fit!(mach, composite=my_composite)
```

最後の2行は次のように等価です。

```julia
mach = machine(ConstantClassifier(), X, y)
fit!(mach)
```

モデルの指定を遅延させることは、学習ネットワークを新しいスタンドアロンモデルタイプとしてエクスポートする際に使用されます。[`prefit`](@ref)および学習ネットワークに関するMLJのドキュメントを参照してください。

[`fit!`](@ref)、[`default_scitype_check_level`](@ref)、[`MLJBase.save`](@ref)、[`serializable`](@ref)も参照してください。
