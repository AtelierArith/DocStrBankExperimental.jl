```
SchildsLadderTransport <: AbstractVectorTransportMethod
```

[`schilds_ladder`](@ref)をベクトル輸送法として[`vector_transport_to`](@ref)または[`vector_transport_direction`](@ref)内で使用するように指定します。すなわち、

$$
X∈ T_p\mathcal M
$$

を点$p∈\mathcal M$での接ベクトル、$q∈\mathcal M$を輸送先の点とします。すると、

$$
P^{\mathrm{S}}_{q\gets p}(X) =
    \log_q\bigl( \operatorname{retr}_p ( 2\operatorname{retr}_p^{-1}c ) \bigr),
$$

ここで$c$は$q$と$d=\exp_pX$の中点です。

この方法は、マニフォールドを離れないようにする内部関数[`schilds_ladder`](@ref)`(M, p, d, q)`を使用します。

この名前は、繰り返し適用することで得られる平行四辺形の画像が梯子の画像になることに由来します。この近似は[EhlersPiraniSchild:1972](@cite)で提案されました。

# コンストラクタ

```julia
SchildsLadderTransport(
    retraction = ExponentialRetraction(),
    inverse_retraction = LogarithmicInverseRetraction(),
)
```

expとlogを使用する古典的なSchildの梯子を構築します。すなわち、[EhlersPiraniSchild:1972](@cite)で提案されたように。さらに安価な輸送のために、これらの内部操作はそれぞれ[`AbstractRetractionMethod`](@ref) `retraction`および[`AbstractInverseRetractionMethod`](@ref) `inverse_retraction`に変更できます。
