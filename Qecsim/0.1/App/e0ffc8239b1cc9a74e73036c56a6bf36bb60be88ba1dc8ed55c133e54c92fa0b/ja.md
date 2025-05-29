```
qec_run_once(
    code, error_model, decoder, p::Real, rng::AbstractRNG=GLOBAL_RNG
) -> RunResult
```

安定器コードのエラー復号回復（理想的）シミュレーションを実行し、実行結果を返します。

パラメータ `code`、`error_model` および `decoder` は、それぞれ [`StabilizerCode`](@ref)、[`ErrorModel`](@ref) および [`Decoder`](@ref) の具体的なサブタイプまたはダックタイピングされた実装である必要があります。

シミュレーションアルゴリズムは次のとおりです。

1. $$
    S ←
    $$

    `stabilizers(code)`
2. $$
    L ←
    $$

    `logicals(code)`
3. $$
    e ←
    $$

    `generate(error_model, code, p, rng)`
4. $$
    y ← S ⊙ e
    $$
5. `decode_result` $←$ `decode(decoder, code,` $y$`; kwargs...)`
6. $$
    r ←
    $$

    `decode_result.recovery`
7. サニティチェック: $S ⊙ (r ⊕ e) = 0$
8. `logical_commutations` $← L ⊙ (r ⊕ e)$
9. `success` $← L ⊙ (r ⊕ e) = 0$

ここで、$⊕$ は要素ごとの排他的論理和を示し、$⊙$ は [`PauliTools.bsp`](@ref bsp) で定義されています。

[`decode`](@ref) に渡される `kwargs` には `error_model`、`p` および `error` が含まれます。ほとんどのデコーダはこれらのパラメータを無視します。[`decode`](@ref) メソッドは [`DecodeResult`](@ref) を返します。`decode_result.success` および/または `decode_result.logical_commutations` が指定されている場合、それらは `success` および `logical_commutations` の値を上書きします。`decode_result.recovery` が指定されているかどうかにかかわらず、`decode_result.custom_values` の値は実行結果に渡されます。

[`RunResult`](@ref) も参照してください。

# 例

```jldoctest
julia> using Qecsim.BasicModels, Qecsim.GenericModels, Random

julia> rng = MersenneTwister(6);  # 再現可能な結果のために乱数シードを使用

julia> qec_run_once(FiveQubitCode(), DepolarizingErrorModel(), NaiveDecoder(), 0.2, rng)
RunResult{Nothing}(false, 2, Bool[1, 0], nothing)
```
