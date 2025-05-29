```
(new_trace, accepted) = metropolis_hastings(
    trace, proposal::GenerativeFunction, proposal_args::Tuple,
    involution::Union{TraceTransformDSLProgram,Function};
    check=false, observations=EmptyChoiceMap())
```

選択マップの空間に対する逆写像（その逆自身である全単射）に基づいて一般化された（可逆ジャンプ）メトロポリス・ヘイスティングス更新を実行し、新しいトレース（移動が受け入れられなかった場合は前のトレースと等しい）と、移動が受け入れられたかどうかを示すBoolを返します。

ほとんどのユーザーは、[`@transform`](@ref)マクロを使用して[Trace Transform DSL](@ref)を使用して`involution`を構築したいと考えるでしょうが、ユーザーがより制御できるように、次のシグネチャを持つJulia関数を`involution`として提供することも可能です。

```
(new_trace, bwd_choices::ChoiceMap, weight) = involution(trace::Trace, fwd_choices::ChoiceMap, fwd_retval, fwd_args::Tuple)
```

生成関数`proposal`は、引数`(trace, proposal_args...)`で実行され、選択マップ`fwd_choices`と戻り値`fwd_ret`を生成します。モデル引数（`trace`に含まれる）と`proposal_args`の各値に対して、`involution`関数は、タプル`(get_choices(trace), fwd_choices)`をタプル`(get_choices(new_trace), bwd_choices)`にマッピングする逆写像を適用します。`fwd_ret`は`fwd_choices`と`proposal_args`の決定論的関数であることに注意してください。離散的なランダム選択のみが使用される場合、`weight`は`get_score(new_trace) - get_score(trace)`と等しくなければなりません。

連続的なランダム選択が使用される場合、逆写像によって返される`weight`は、離散的なランダム選択に対する逆写像をカリー化することによって得られる連続的なランダム選択に対する全単射のヤコビ行列の行列式である加法的補正項を含む必要があります（この補正項は、[Trace Transform DSL](@ref)を使用して逆写像が構築されると自動的に計算されます）。注意：連続的なランダム選択に対する全単射のヤコビ行列はフルランクでなければなりません（すなわち、行列式がゼロでない）。逆写像に対する`check`キーワード引数は、逆写像が実行する動的正確性チェックを有効または無効にするために使用できます。成功した実行の場合、`check`は戻り値を変更しません。
