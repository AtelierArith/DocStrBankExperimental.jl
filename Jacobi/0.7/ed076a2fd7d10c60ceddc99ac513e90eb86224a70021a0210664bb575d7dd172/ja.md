```
legendre(x, b)
```

レジェンドル多項式を計算します。

レジェンドル多項式は、パラメータ a と b がゼロのジャコビ多項式です。

`jacobi` と同じインターフェースです。`dlegendre` はレジェンドル多項式の導関数を計算します。

# 例

```julia-repl
julia> x = legendre(0.4, 5)
0.27063999999999994

julia> x = legendre(2//5, 5)
3383//12500

julia> x = dlegendre(0.4, 5)
-1.3170000000000002

julia> x = dlegendre(2//5, 5)
-1317//1000
```
