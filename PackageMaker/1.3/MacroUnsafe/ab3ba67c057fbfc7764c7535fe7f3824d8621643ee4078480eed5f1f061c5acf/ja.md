```
@unsafe
```

Ubuntu 24のアップストリームバグに対する回避策です。これにより、Electronでのサンドボックスが無効になります。このマクロを`gogui()`を呼び出す前に実行してください。

ただし、Ubuntu 24でPackageMakerを使用する推奨方法は、VSCodeから使用することであり、この場合は`@unsafe`を呼び出さずに正常に動作します。

# 例

```julia-repl
julia> @unsafe;
julia> gogui()
```
