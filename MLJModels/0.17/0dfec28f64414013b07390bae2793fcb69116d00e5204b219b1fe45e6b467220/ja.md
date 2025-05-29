```
@load ModelName pkg=nothing verbosity=0 add=false
```

最初の引数で指定されたモデル名のモデルタイプを呼び出しモジュールにインポートし、同名のモデルタイプを提供するパッケージがある場合は`pkg`を指定します。モデルタイプを返します。

**警告** 古いバージョンのMLJ/MLJModelsでは、`@load`は*インスタンス*を返していました。

現在の環境に必要なインターフェースパッケージを自動的に追加するには、`add=true`を指定します。インタラクティブな読み込みには、代わりに`@iload`を使用してください。

### 例

```
Tree = @load DecisionTreeRegressor
tree = Tree()
tree2 = Tree(min_samples_split=6)

SVM = @load SVC pkg=LIBSVM
svm = SVM()
```

詳細は[`@iload`](@ref)を参照してください。
