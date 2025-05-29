```
circle(centerpoint::Point, r; action=:none)
circle(centerpoint::Point, r, action)
```

半径 `r` の円を 'centerpoint' を中心に作成し、現在のパスに追加します。

`action` は `do_action()` によって適用されるアクションの一つで、デフォルトは `:none` です。

円を囲むバウンディングボックスのコーナーである2つの点のタプルを返します。

円を描画し、中心点によって配置するには `ellipse()` を使用することもできます。

`circlepath()` はベジェ曲線を使用して円を構築し、現在のパスに追加します。

`squircle()` はスーパーレップスを構築します。 `polysuper()` はスーパシェイプを構築し、スーパーレップスの一般化です。

`juliacircles()` はお馴染みの形で3つの円を描画します。

他にも: `arc()`, `arc2r()`, `arc2sagitta()`, `carc()`, `carc2r()`, `carc2sagitta()`, `circlering()`, `crescent()`, `curve()`, `spiral()`, などがあります。
