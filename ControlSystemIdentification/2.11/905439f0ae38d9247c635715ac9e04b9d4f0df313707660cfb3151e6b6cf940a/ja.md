```
tfest(
    data::FRD,
    p0,
    link = log ∘ abs;
    freq_weight = sqrt(data.w[1]*data.w[end]),
    refine = true,
    opt = BFGS(),
    opts = Optim.Options(
        store_trace       = true,
        show_trace        = true,
        show_every        = 1,
        iterations        = 100,
        allow_f_increases = false,
        time_limit        = 100,
        x_tol             = 0,
        f_tol             = 0,
        g_tol             = 1e-8,
        f_calls_limit     = 0,
        g_calls_limit     = 0,
    ),
)
```

周波数領域データにパラメトリック伝達関数をフィットさせます。

最初の最適化段階では次の問題を解きます。

$$
\operatorname{minimize}_{B,A}{|| B/l - A||}
$$

2段階目（`refine=true`の場合）では次の問題を解きます。

$$
\operatorname{minimize}_{B,A}{|| \text{link}\left(\dfrac{B}{A}\right) - \text{link}\left(l\right)||}
$$

(`abs2(link(B/A) - link(l))`)

# 引数:

  * `data`: 周波数領域データを持つ`FRD`オブジェクト。
  * `p0`: 初期パラメータの推測。`NamedTuple`または`ComponentVector`で、`tf`への呼び出しに現れる分子と分母を指定する`b,a`フィールドを持つことができます。すなわち、`(b = [1.0], a = [1.0,1.0,1.0])`のように。`TransferFunction`のインスタンスでも構いません。
  * `link`: デフォルトでは、フィッティング中に位相情報は破棄されます。位相を含めるには、`link = log`に変更します。
  * `freq_weight`: 逆周波数で重み付けを適用します。この値は、重みが一定であるカットオフ周波数を決定し、その後重みが線形に減少します。デフォルトでは、最小周波数と最大周波数の幾何平均です。
  * `refine`: 最初の結果を洗練するために2段階目の最適化が行われるかどうかを示します。
  * `opt`: 使用するOptimオプティマイザ。
  * `opts`: ソルバーオプションを制御する`Optim.Options`。

最小位相系を最小位相に変換するための[`minimum_phase`](@ref)も参照してください。
