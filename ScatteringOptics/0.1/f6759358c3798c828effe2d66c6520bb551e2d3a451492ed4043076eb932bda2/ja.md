```
phase_screen(psm::AbstractPhaseScreen, λ_cm, noise_screen=nothing)
```

StationaryRandomFields.jlのパワーローノイズ手法を使用して、屈折位相スクリーン`ϕ`を生成します。与えられない場合はガウスノイズスクリーンがデフォルトとなる2Dノイズ*スクリーンは、入力AbstractPhaseScreen `psm`で定義されたパワーロー`Q`によってスケーリングされます。観測波長`λ*cm`は指定する必要があります。
