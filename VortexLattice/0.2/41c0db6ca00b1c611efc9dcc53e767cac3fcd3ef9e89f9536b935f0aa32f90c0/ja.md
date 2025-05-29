```
`import_vsp(comp::vsp.VSPComponent; geomType::String="", optargs...)
```

OpenVSPコンポーネントからVortexLatticeオブジェクトにプロパティをインポートします。プロペラおよびダクトのジオメトリのインポートは開発中です。

**引数**

  * `comp::VSPGeom.VSPComponent`: 単一の`VSPGeom.VSPComponent`オブジェクト
  * `geomType::String` : ジオメトリタイプは以下のいずれかである必要があります - `wing`, `fuselage`, `prop`, `duct`
  * `optargs` : 内部で呼び出されるgrid*to*surface_panels()に渡されるオプション引数

**戻り値**

  * `grid`: パネルコーナーを含む次元(3, i, j)の配列
  * `surface`: 生成されたパネルを含む次元(i, j)の配列

```
