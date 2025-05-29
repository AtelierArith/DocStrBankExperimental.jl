```
CUDALibs()
CUDALibs(settings)
```

CUDAライブラリを使用して計算を実行することを示します。オプションで、アルゴリズム設定を指定するオブジェクトを渡すことができます。

# 例:

```julia
filter(CUDALibs(), image, kernel)
filter(CUDALibs(backend), image, kernel)
```
