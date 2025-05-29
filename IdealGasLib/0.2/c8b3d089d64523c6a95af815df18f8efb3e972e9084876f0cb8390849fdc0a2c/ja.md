`(rebase(𝐻::nobleGasHeat{𝕡,𝕩}, 𝑇::T_amt{𝕡,𝕩}, 𝑃::P_amt{𝕡,𝕩})::nobleGasHeat{𝕡,𝕩}) where {𝕡,𝕩}`

`𝐻`に基づいて`nobleGasHeat`インスタンスを返し、`(Tref, Pref) = (𝑇, 𝑃)`とし、同じ`(T, P)`状態に対して同じエントロピー値を得るように`sref`を調整します。`s°`の値も`𝐻.Pref == 𝑃`の場合にのみ一致します。
