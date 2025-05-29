```
reinit!(integrator::DEIntegrator,args...; kwargs...)
```

reinit関数は、新しい値で積分を再起動することを可能にします。

# 引数

  * `u0`: 開始する`u`の値。デフォルト値は`integrator.sol.prob.u0`です。

# キーワード引数

  * `t0`: 開始時点。デフォルト値は`integrator.sol.prob.tspan[1]`です。
  * `tf`: 終了時点。デフォルト値は`integrator.sol.prob.tspan[2]`です。
  * `erase_sol=true`: 他の値を解に持たずに開始するか、前の解を保持するか。
  * `tstops`, `d_discontinuities`, & `saveat`: これらが保存されるキャッシュ。デフォルトは元のキャッシュです。
  * `reset_dt`: 自動`dt`決定アルゴリズムを使用して現在の`dt`の値をリセットするかどうかを設定します。デフォルトは`(integrator.dtcache == zero(integrator.dt)) && integrator.opts.adaptive`です。
  * `reinit_callbacks`: コールバック初期化を再実行するかどうかを設定します（`initialize_save`はそのためのものです）。デフォルトは`true`です。
  * `reinit_cache`: キャッシュ初期化関数を再実行するかどうかを設定します（すなわち、FSALをリセットし、ベクトルを割り当てないこと）。通常は正確性のために`true`であるべきです。デフォルトは`true`です。

さらに、[`auto_dt_reset!`](@ref)にアクセスすることで、自動`dt`初期化アルゴリズムを実行できます。
