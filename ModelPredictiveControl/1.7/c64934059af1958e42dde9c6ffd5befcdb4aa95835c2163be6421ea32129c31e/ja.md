```
InternalModel(model::SimModel; i_ym=1:model.ny, stoch_ym=ss(I,I,I,I,model.Ts))
```

`model`（[`LinModel`](@ref）または[`NonLinModel`](@ref））に基づいて内部モデル推定器を構築します。

`i_ym`は、測定された出力$\mathbf{y^m}$の`model`出力インデックスを提供し、残りは未測定の$\mathbf{y^u}$です。`model`は決定論的予測$\mathbf{ŷ_d}$を評価し、`stoch_ym`は測定された出力の確率的予測$\mathbf{ŷ_s^m}$（未測定のものは$\mathbf{ŷ_s^u=0}$）を評価します。予測出力は両方の値を合計します：$\mathbf{ŷ = ŷ_d + ŷ_s}$。詳細については拡張ヘルプを参照してください。この推定器は、`model`のシミュレーションがメモリを割り当てない場合に限り、割り当てなしです。

!!! warning
    `InternalModel`推定器は、`model`が統合中または不安定な場合には機能しません。コンストラクタは`LinModel`のこれらの側面を検証しますが、`NonLinModel`については検証しません。そのような場合には、他の状態推定器を使用してください。


# 例

```jldoctest
julia> estim = InternalModel(LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5), i_ym=[2])
InternalModel推定器、サンプル時間Ts = 0.5 s、LinModelおよび：
 1 操作入力u
 2 推定状態x̂
 1 測定出力ym
 1 未測定出力yu
 0 測定された外乱d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    `stoch_ym`は、$\mathbf{y^m}$の外乱をモデル化する`TransferFunction`または`StateSpace`オブジェクトです。その入力は、仮想的な平均ゼロのホワイトノイズベクトルです。`stoch_ym`は、デフォルトで測定された出力ごとに1つの積分器を仮定し、現在の確率的推定$\mathbf{ŷ_s^m}(k) = \mathbf{y^m}(k) - \mathbf{ŷ_d^m}(k)$が将来にわたって一定であると仮定します。これは動的行列制御（DMC）戦略であり、シンプルですが時には攻撃的すぎることがあります。`stoch_ym`に追加の極と零点を設けることでこれを緩和できます。以下のブロックダイアグラムは、内部モデル構造を要約しています。

    ![内部モデル構造のブロックダイアグラム](../assets/imc.svg)


```
