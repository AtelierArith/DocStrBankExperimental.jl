```
bdplot(x; kwargs...) → fig, ax
bdplot!(ax::Axis, x; kwargs...)
```

`DynamicalBilliards`からオブジェクト`x`を指定された軸（または新しい図）にプロットします。`x`は障害物、粒子、粒子のベクトル、またはビリヤードであることができます。

```
bdplot!(ax,::Axis, o::Obstacle; kwargs...)
```

キーワードは`lines!`または`poly!`に伝播されます。関数`obfill, obcolor, obls, oblw`（エクスポートされていない）は、障害物をプロットする際の線の色、塗りつぶしの色、線のスタイル、線の幅のグローバルデフォルトを決定します。

```
bdplot!(ax,::Axis, bd::Billiard; clean = true, kwargs...)
```

`clean = true`の場合、すべての軸要素が削除され、等しいアスペクト比が確立されます。他のキーワードは障害物プロットに伝播されます。

```
bdplot!(ax,::Axis, bd::Billiard, xmin, xmax, ymin, ymax; kwargs...)
```

この呼び出しシグネチャは周期的ビリヤードをプロットします：`bd`をその周期ベクトルに沿ってプロットし、`xmin, xmax, ymin, ymax`で指定された空間の総量を埋めるようにします。

```
bdplot!(ax,::Axis, ps::Vector{<:AbstractParticle}; kwargs...)
```

粒子を散布図（位置）およびベクトル場プロット（速度）としてプロットします。キーワード`particle_size = 5, velocity_size = 0.05`はプロットされた粒子のサイズを設定します。キーワード`colors = JULIADYNAMICS_CMAP`は粒子の色を決定し、カラーマップまたは`ps`と同じ長さの色のベクトルのいずれかであることができます。残りのキーワードは粒子の散布図に伝播されます。
