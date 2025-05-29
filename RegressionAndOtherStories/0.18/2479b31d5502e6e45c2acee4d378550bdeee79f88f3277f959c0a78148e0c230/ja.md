# ros_datadir()

RegressionAndOtherStories.jl データファイルへのパス。

RegressionAndOtherStories.jl のデータセットへのパスを構築します。

## 位置引数

```julia
* `parts::Vector{AbstractString}` # データファイルへのパス
```

### 戻り値

```julia
* `path::AbstractString` # パスまたは ""。
```

# 拡張ヘルプ

例:

```julia
ros_datadir("ElectionsEconomy", "hibbs.dat")
```

または、DataFrame として読み込むには:

```julia
hibbs = CSV.read(ros_datadir("ElectionsEconomy", "hibbs.csv"), DataFrame)
```
