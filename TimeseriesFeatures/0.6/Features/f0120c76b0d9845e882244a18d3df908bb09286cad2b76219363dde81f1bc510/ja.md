```
𝑓 = Feature([;] method::Function, name=Symbol(method), keywords="", description="")
```

`Feature`を構築します。これは、`name`、`keywords`、および短い`description`で注釈された関数です。特徴は関数として呼び出すことができ、`getname(𝑓)`、`getkeywords(𝑓)`、および`getdescription(𝑓)`を使用して注釈にアクセスできます。この関数は、少なくとも`AbstractVector`用のメソッドを持っている必要があります。ベクトルに対するメソッドは、`Matrix`入力に対して列ごとに適用され、`Matrix`に対して定義された関数メソッドに関係なく適用されます。

# 例

```julia
𝑓 = Feature(sum, :sum, ["distribution"], "時系列値の合計")
𝑓(1:10) # == sum(1:10) == 55
getdescription(𝑓) # "時系列値の合計"
```
