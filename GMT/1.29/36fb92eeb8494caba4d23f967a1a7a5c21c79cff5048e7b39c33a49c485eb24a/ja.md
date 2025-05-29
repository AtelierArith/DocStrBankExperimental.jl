```
ablines(a, b; kw...)
```

または

```
ablines([a1, a2, ..., an], [b1, b2, ..., bn]; kw...)
```

または

```
ablines(D::GMTdataset; kw...)
```

Y = a + b * X で定義される直線を作成します。入力は `a,b` パラメータのペアまたはそれらのベクトルであり、この場合は複数の直線がプロットされます。プロットの制限は、通常の `kw` の `region` オプションを通じて渡されるか、欠落している場合は x = [0 10] の範囲で線をプロットします。入力が `GMTdataset` 型の場合の第三の形式は、これが `linearfitxy` 関数で計算されたことを意味し、線形フィットパラメータがデータ型の属性に埋め込まれています。すべての `plot` オプションは `kw` 引数を通じて利用可能です。

# 例:

```julia-repl
ablines([1, 2, 3], [1, 1.5, 2], linecolor=[:red, :orange, :pink], linestyle=:dash, linewidth=2, show=true)
```

```julia-repl
D = linearfitxy([0.0, 0.9, 1.8, 2.6, 3.3, 4.4, 5.2, 6.1, 6.5, 7.4], [5.9, 5.4, 4.4, 4.6, 3.5, 3.7, 2.8, 2.8, 2.4, 1.5],
                 sx = 1 ./ sqrt.([1000., 1000, 500, 800, 200, 80,  60, 20, 1.8, 1]), sy=1 ./
                 sqrt.([1., 1.8, 4, 8, 20, 20, 70, 70, 100, 500]));
plot(D, linefit=true, band_ab=true, band_CI=true, ellipses=true, Vd=2)
plot!(D, linefit=true, Vd=2)
ablines!(D, Vd=2)
ablines!(0,1, Vd=2)
```
