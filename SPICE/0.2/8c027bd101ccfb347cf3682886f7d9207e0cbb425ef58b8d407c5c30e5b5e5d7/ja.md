```
vprjpi(vin, projpl, invpl)
```

指定された平面において、別の平面における指定されたベクトルにマッピングされるベクトルを直交射影の下で見つけます。

### 引数

  * `vin`: 投影されたベクトル
  * `projpl`: `vin`を含む平面
  * `invpl`: `vin`の逆像を含む平面

### 出力

`vin`の逆投影を返すか、`vin`を計算できなかった場合は`nothing`を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/vprjpi_c.html)
