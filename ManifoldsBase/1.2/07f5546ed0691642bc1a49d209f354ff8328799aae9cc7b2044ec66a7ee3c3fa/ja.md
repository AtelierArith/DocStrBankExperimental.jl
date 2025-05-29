```
PoleLadderTransport <: AbstractVectorTransportMethod
```

[`pole_ladder`](@ref)をベクトル輸送法として[`vector_transport_to`](@ref)または[`vector_transport_direction`](@ref)内で使用するように指定します。すなわち、

$$
X∈ T_p\mathcal M
$$

を$p∈\mathcal M$における接ベクトル、$q∈\mathcal M$を輸送先の点とします。次に$x = \exp_pX$を使用して`y =`[`pole_ladder`](@ref)`(M, p, x, q)`を呼び出し、得られたベクトルは$Y = -\log_qy$を計算することで得られます。

[`PoleLadderTransport`](@ref)は[`SchildsLadderTransport`](@ref)と比較して2つの利点があります：

  * 複数のベクトルを輸送したい場合、中央値$c$が変わらないため、評価が安価です。
  * 両方の方法が曲率がゼロの場合に正確である一方で、ポールラダーは対称リーマン多様体においても正確です[Pennec:2018](@cite)。

ポールラダーは[LorenziPennec:2013](@cite)で提案されました。その名前は、連続する点の列に適用したときにポールラダーに似ていることに由来します。

# コンストラクタ

```julia
PoleLadderTransport(
    retraction = ExponentialRetraction(),
    inverse_retraction = LogarithmicInverseRetraction(),
)
```

expとlogを使用する古典的なポールラダーを構築します。すなわち、[LorenziPennec:2013](@cite)で提案されたように。さらに安価な輸送のために、内部操作をそれぞれ[`AbstractRetractionMethod`](@ref) `retraction`および[`AbstractInverseRetractionMethod`](@ref) `inverse_retraction`に変更することができます。
