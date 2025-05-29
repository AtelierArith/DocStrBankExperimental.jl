```
serializable(mach::Machine)
```

マシンの浅いコピーを返し、シリアライズ可能にします。特に、すべてのトレーニングデータが削除され、必要に応じて学習されたパラメータが永続的な表現に置き換えられます。

一般的な目的のJuliaシリアライザは、`serializable`の出力に適用できます（例：JLSO、BSON、JLD）が、使用する前にデシリアライズされたオブジェクト`mach`に対して`restore!(mach)`を呼び出す必要があります。以下の例を参照してください。

Juliaの標準シリアライゼーションライブラリを使用する場合、[`MLJBase.save`](@ref)（または`MLJ.save`）メソッドを使用して、より短いワークフローが利用可能です。

`serializable`によって返されたマシンは、プロパティ`mach.state == -1`によって特徴付けられます。

### [JLSO](https://invenia.github.io/JLSO.jl/stable/)を使用した例

```julia
using MLJ
using JLSO
Tree = @load DecisionTreeClassifier
tree = Tree()
X, y = @load_iris
mach = fit!(machine(tree, X, y))

# このマシンは今やシリアライズ可能です
smach = serializable(mach)
JLSO.save("machine.jlso", :machine => smach)

# デシリアライズして学習されたパラメータを使用可能な形式に復元します：
loaded_mach = JLSO.load("machine.jlso")[:machine]
restore!(loaded_mach)

predict(loaded_mach, X)
predict(mach, X)
```

[`restore!`](@ref)、[`MLJBase.save`](@ref)も参照してください。
