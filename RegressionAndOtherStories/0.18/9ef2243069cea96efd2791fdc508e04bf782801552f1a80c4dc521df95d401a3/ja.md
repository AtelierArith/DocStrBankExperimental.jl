ros_data()

RパッケージROS-Examplesのデータファイルへのパスの基本部分。`env_var`がENVに存在しない場合は""を返します。

## 位置引数

```julia
* `dataset::Union{AbstractString, Missing}` # ROS-Examples内のデータへのパス
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
ros_path()
ros_path("HDI")
```
