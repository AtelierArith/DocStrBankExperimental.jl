```
 function quiverdata(rastercoord,
                     rasterflux;
                     vscale = 1.0,
                     vnormalize = true,
                     vconstant = false)
```

[`vectorsample`](@ref)によって得られたラスタグリッドからクイバープロット用の非ゼロフラックスを抽出します。

qc, qv - `d x nquiver` 行列を返します。

vnormalizeがtrueの場合、ベクトルフィールドはvscale*min(spacing)に正規化されます。そうでない場合は、vscaleによってスケーリングされます。結果データは、さまざまなプロットバックエンドを使用して`quiver`に渡す準備ができています。
