```
FV = translate(FV::GMTfv; dx=0.0, dy=0.0, dz=0.0) -> GMTfv
```

FacesVerticesオブジェクトをdx、dy、dzだけ移動します。

*insitu*バージョンの`translate!()`は、インプレースで実行します。

### 引数

  * `FV::GMTfv`: FacesVerticesオブジェクト

### キーワード引数

  * `dx, dy, dz`: x、y、zのFV.vertsコンポーネントに適用するオフセットの量。
