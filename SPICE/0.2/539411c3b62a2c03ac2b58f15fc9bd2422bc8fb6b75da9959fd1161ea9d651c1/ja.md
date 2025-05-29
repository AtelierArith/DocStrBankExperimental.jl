```
spkaps(targ, et, ref, abcorr, stobs, accobs)
```

観測者の状態と加速度を太陽系重心に対して与えられた場合、光時間と星の収差をオプションで補正した、観測者に対するターゲット天体の状態（位置と速度）を返します。すべての入力および出力ベクトルは慣性参照フレームに対して表現されます。

ユーザーは通常、このルーチンではなく、高レベルAPIルーチン[`spkezr`](@ref)または[`spkez`](@ref)を呼び出すべきです。

### 引数

  * `targ`: ターゲット天体。
  * `et`: 観測者のエポック。
  * `ref`: 出力状態の慣性参照フレーム。
  * `abcorr`: 収差補正フラグ。
  * `stobs`: SSBに対する観測者の状態。
  * `accobs`: SSBに対する観測者の加速度。

### 出力

  * `starg`: ターゲットの状態。
  * `lt`: 観測者とターゲットの間の一方向の光時間。
  * `dlt`: 時間に対する光時間の導関数。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkaps_c.html)

```
