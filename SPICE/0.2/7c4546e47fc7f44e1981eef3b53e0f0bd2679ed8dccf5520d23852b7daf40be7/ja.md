```
isrot(m, ntol, dtol)
```

3×3 行列が回転行列であるかどうかを示します。

### 引数

  * `m`: テストする行列
  * `ntol`: `m` の列のノルムに対する許容誤差
  * `dtol`: `m` の単位化された列からなる行列の行列式に対する許容誤差

### 出力

`m` が回転行列である場合は `true` を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/isrot_c.html)
