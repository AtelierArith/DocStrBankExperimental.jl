```
@mix_proposals weight1 propose1 weight2 propose2 ...
```

提案関数を生成するマクロで、提供された確率重みのもとで提供された関数の中からランダムに選択します。[`LocalSampler`](@ref)と一緒に使用します。

# 例

```julia
# 提案関数は、40%の確率でスピンフリップを提案し、60%の確率で
# ガウス摂動を提案します。
@mix_proposals 0.4 propose_flip 0.6 propose_delta(0.2)
```
