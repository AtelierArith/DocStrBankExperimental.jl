```
ParameterAggregator(parfullnames::Vector{String}, model; eltype=Float64) -> ParameterAggregator
```

`parfullnames`で指定されたモデルパラメータのサブセットをフラットなベクターとして表現します。

`parfullnames`は、モデルパラメータのサブセットを定義する形式のベクター `["domainname.reactionname.parname", ...]` です（注：`ParDouble` または `ParDoubleVec` 型でなければなりません。つまり、Float64のスカラーまたはベクターです）。

`norm_values`は、フラットなパラメータベクターの正規化を指定するために使用できます（デフォルトは1.0です）。

次のようにして、パラメータをフラットなベクターから設定したり、コピーしたりできます：

```
copyto!(pa::ParameterAggregator, newvalues::Vector)  # newvalues .* norm_values から設定
copyto!(currentvalues::Vector, pa::ParameterAggregator) # currentvaluesにコピーし、norm_valuesで割る
get_currentvalues(pa::ParameterAggregator) -> currentvalues::Vector
```

パラメータのサブセットは、SciMLソルバーによって使用される `p` パラメータベクターによって定義され、完全なセット（yamlファイルから）と組み合わされて、例えばODEを解いて感度研究を可能にします。

`eltype`は、パラメータのヤコビアンのためにForwardDiff自動微分をサポートするデュアル数などにすることができます。
