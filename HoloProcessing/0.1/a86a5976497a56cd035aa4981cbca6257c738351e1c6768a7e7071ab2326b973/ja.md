```
load_holo(PATH::String, name::String; convert=true) -> AbstractMatrix
```

与`画像`路径以及`画像`的名称(包括后缀)相关，实现对全息图的载入

# Arguments

  * `PATH`: `画像`所在路径
  * `name`: `画像`的名称，比如`tail.bmp`
  * `convert`: 可选参数，默认值是`true`。当为`true`时，该函数返回`画像`的灰度值浮点数矩阵；当为`false`时，该函数直接返回画像
