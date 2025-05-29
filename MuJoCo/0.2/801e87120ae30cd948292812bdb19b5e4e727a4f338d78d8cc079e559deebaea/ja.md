```
mj_normalizeQuat(m, qpos)
```

qpos型ベクトル内のすべてのクォータニオンを正規化します。

# 引数

  * **`m::Model`** -> 定数。
  * **`qpos::Vector{Float64}`** -> 可変サイズのベクトル。`qpos`はベクトルである必要があり、行列ではありません。`qpos`はサイズnqである必要があります。
