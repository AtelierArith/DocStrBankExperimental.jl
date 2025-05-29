```
ArrayFireLibs()
ArrayFireLibs(settings)
```

ArrayFireライブラリを使用して計算を実行することを示します。オプションで、アルゴリズム設定を指定するオブジェクトを渡すことができます。

# 例:

```julia
filter(ArrayFireLibs(), image, kernel)
filter(ArrayFireLibs(backend), image, kernel)
```
