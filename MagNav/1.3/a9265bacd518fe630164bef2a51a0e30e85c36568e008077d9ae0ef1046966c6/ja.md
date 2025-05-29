```
plot_events!(p1::Plot, t::Real, lab::String = "";
             legend::Symbol = :outertopright)
```

既存のプロットにフライト中のイベントをプロットします。

**引数:**

  * `p1`:     プロット（すなわち、データの時系列）
  * `t`:      フライト中のイベントの時間
  * `lab`:    （オプション）フライト中のイベント（凡例）ラベル
  * `legend`: （オプション）凡例の位置（例: `:topleft`, `:outertopright`）

**戻り値:**

  * `nothing`: フライト中のイベントが `p1` にプロットされます。
