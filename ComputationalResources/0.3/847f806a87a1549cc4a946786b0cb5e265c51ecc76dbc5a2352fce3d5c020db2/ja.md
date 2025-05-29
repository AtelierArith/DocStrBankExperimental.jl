```
OpenCLLibs()
OpenCLLibs(settings)
```

計算はOpenCLライブラリを使用して行うべきであることを示します。オプションで、アルゴリズム設定を指定するオブジェクトを渡すことができます。

# 例:

```julia
filter(OpenCLLibs(), image, kernel)
filter(OpenCLLibs(backend), image, kernel)
```
