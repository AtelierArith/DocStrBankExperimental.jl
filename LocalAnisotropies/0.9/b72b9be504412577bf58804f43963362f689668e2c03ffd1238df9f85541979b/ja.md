```
RotationRule(order, motion, radian, main, extrinsic)
```

楕円体回転のルールを作成します

  * order     - 回転が行われる3つの軸の順序; 例: `:ZXZ`
  * motion    - 3つの回転それぞれが時計回り(`:CW`)か反時計回り(`:CCW`)かを示します。右手の法則: 軸の負の方向を向いているときの動きが定義されます
  * radian    - 入力角度がラジアンの場合は`true`、度の場合は`false`
  * main      - 主半軸が`:x`か`:y`かを示します
  * extrinsic - 回転が外的であれば`true`、内的であれば`false`

## 例

GSLIB回転を再現するための回転ルール

```julia
rule = RotationRule(:ZXY,[:CW,:CCW,:CCW],false,:y,false)
```

## 規約

いくつかの回転規約が組み込まれています:

  * `:TaitBryanExtr` => ZXY軸による外的右手回転
  * `:TaitBryanIntr` => ZXY軸による内的右手回転
  * `:EulerExtr`     => ZXZ軸による外的右手回転
  * `:EulerIntr`     => ZXZ軸による内的右手回転
  * `:GSLIB`         => GSLIBソフトウェア回転規約
  * `:Leapfrog`      => Leapfrogソフトウェア回転規約
  * `:Datamine`      => Datamineソフトウェア回転規約、軸の順序ZXZ
  * `:Datamine313`   => Datamineソフトウェア回転規約、軸の順序ZXZ
  * `:Datamine321`   => Datamineソフトウェア回転規約、軸の順序ZYX
  * `:Datamine312`   => Datamineソフトウェア回転規約、軸の順序ZXY
  * `:Datamine323`   => Datamineソフトウェア回転規約、軸の順序ZYZ
