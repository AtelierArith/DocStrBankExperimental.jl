# 拡張ヘルプ

```
σ(d::AbstractVector, L::LineSegment)
```

### アルゴリズム

ベクトル $q - p$ と $d$ の間の角度が90°より大きく、270°より小さい場合（反時計回りの順序で測定）、結果は $p$ になります。それ以外の場合は $q$ になります。角度がちょうど90°または270°の場合、または方向のノルムがゼロの場合、この実装は $q$ を返します。
