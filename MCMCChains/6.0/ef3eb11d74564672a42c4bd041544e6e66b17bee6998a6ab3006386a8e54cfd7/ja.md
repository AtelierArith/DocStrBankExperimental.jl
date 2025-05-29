```
sample([rng,] chn::Chains, [wv::AbstractWeights,] n; replace=true, ordered=false)
```

プールされた (!) チェーン `chn` から `n` サンプルをサンプリングします。

キーワード引数 `replace` と `ordered` は、それぞれサンプリングが置換ありで行われるかどうか、サンプルが順序付きであるかどうかを決定します。指定された場合、サンプリング確率は重み `wv` に比例します。

!!! note
    `chn` に複数のチェーンが含まれている場合、サンプリングの前にそれらはプールされます（すなわち、追加されます）。これにより、この場合でも正確に `n` サンプルが返されることが保証されます：

    ```jldoctest
    julia> chn = Chains(randn(11, 4, 3));

    julia> size(sample(chn, 7)) == (7, 4, 1)
    true
    ```

