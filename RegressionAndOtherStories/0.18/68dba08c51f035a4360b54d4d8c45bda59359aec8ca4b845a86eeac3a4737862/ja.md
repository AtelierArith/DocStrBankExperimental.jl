ros_data()

RパッケージROS-Examples内のデータファイルへのパスを構築します。`env_var`がENVに存在しない場合は""を返します。

## 位置引数

```julia
* `dataset::AbstractString`
* `parts::Vector{AbstractString}` # データファイルへのパス
```

### キーワード引数

```julia
* `env_var = "JULIA_ROS_HOME"` # 環境変数名
```

### 戻り値

```julia
* `path::AbstractString` # パスまたは""。
```

# 拡張ヘルプ

例:

```julia
ros_data()
ros_data("HDI", "hdi.dat")
```
