```
C, kp, ki, fig, CF = loopshapingPI(P, ωp; ϕl, rl, phasemargin, form=:standard, doplot=false, Tf, F)
```

PIコントローラのパラメータ（並列形式）を選択し、周波数`ωp`における`P`のナイキスト曲線を`rl exp(i ϕl)`に移動させます。

パラメータは、`form`によって選択された一般的な表現の1つとして返されます。オプションは次のとおりです。

  * `:standard` - $K_p(1 + 1/(T_i s) + T_d s)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$

`phasemargin`が指定されている場合（度数で）、`ϕl`は曲線が`phasemargin - 180`度の角度に移動するように選択されます。

`rl`が指定されていない場合、`ωp`における曲線の大きさは同じままで、位相のみが影響を受けます。同様に、`phasemargin`が指定されていない場合は`ϕl`も同様です。

  * `Tf`: コントローラを厳密に適切にするための、形式`tf(1, [Tf^2, 2*Tf/sqrt(2), 1])`の二次測定ノイズフィルタのオプションの時間定数。
  * `F`: `Tf`が指定されている場合に使用されるデフォルトの二次フィルタの代わりに使用する事前設計されたフィルタ。
  * `doplot`: システムの`gangoffourplot`および`nyquistplot`をプロットします。

[`loopshapingPID`](@ref)、[`pidplots`](@ref)、[`stabregionPID`](@ref)、および[`placePI`](@ref)も参照してください。
