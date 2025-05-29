```
FV = rotate(FV::GMTfv, a=Float64[]; rx=0.0, ry=0.0, rz=0.0) -> GMTfv
```

FacesVertices `FV`をオイラー角（度単位）`rx`、`ry`、`rz`で回転させます。

*insitu* バージョン `rotate!()` はインプレースで実行します。注意: 回転後、表面が必ずしも反時計回り（CCW）であるとは限らないため、`bfculling` の値を false に設定します。

### 引数

  * `FV::GMTfv`: FacesVertices オブジェクト
  * `a=[rx, ry, rz]`: x、y、z 軸に関するオイラー角（度単位）。

### キーワード引数

  * `rx, ry, rz`: `a` の代わりに、これらのオイラー角のうち1つから3つを提供します。
