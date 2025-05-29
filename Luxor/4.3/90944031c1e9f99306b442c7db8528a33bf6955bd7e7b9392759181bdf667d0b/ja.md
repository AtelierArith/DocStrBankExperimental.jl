```
box(pt, width, height, cornerradii::Array; action=:none)
box(pt, width, height, cornerradii::Array, action=:none)
```

点 `pt` を中心に幅 `width` と高さ `height` のボックス/長方形を描き、配列 `cornerradii` の対応する値で各コーナーを丸めます。

構築されたパスは弧と直線で構成されています。

最初のコーナーは左下、次は左上、その次は右上、最後は右下です。

## 例

```julia
@draw begin
    box(O, 120, 120, [0, 20, 40, 60], :fill)
end
```
