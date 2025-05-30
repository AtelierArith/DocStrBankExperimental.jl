```
wiggle!(wav[; taxis, zaxis, sc, EdgeColor, FaceColor, Orient, Overlap, ZDir])
wiggle!(plt, wav[; taxis, zaxis, sc, EdgeColor, FaceColor, Orient, Overlap, ZDir])
```

現在表示されているグラフィックス上または `plt` の上にシェーディングされたウィグルをプロットします。現在利用可能な表示グラフィックスがない場合、新しい `Plots.Plot` オブジェクトが生成され、シェーディングされたウィグルがプロットされます。

# 引数

  * `plt::Plots.Plot`: シェーディングされたウィグルをプロットするための入力プロット。
  * `wav::AbstractArray{<:Number,2}`: 波形列の行列。

# キーワード引数

  * `taxis::AbstractVector`: (デフォルト: `1:size(wav,1)`) 時間軸ベクトル
  * `zaxis::AbstractVector`: (デフォルト: `1:size(wav,2)`) 空間軸ベクトル
  * `sc::Real`: (デフォルト: `1`) スケールファクター/拡大率。
  * `EdgeColor::Symbol`: (デフォルト: `:black`) ウィグルのエッジの色を設定します。
  * `FaceColor::Symbol`: (デフォルト: `:black`) ウィグルのシェーディング色を設定します。
  * `Overlap::Bool`: (デフォルト: `true`) 信号のスケーリング方法。

      * `true`  - 信号が重なる（デフォルト）;
      * `false` - 信号が重ならないようにスケーリングされます。
  * `Orient::Symbol`: (デフォルト: `:across`) ウィグルの向きを制御します。

      * `:across` - 左から右へ
      * `:down`   - 上から下へ
  * `ZDir::Symbol`: (デフォルト: `:normal`) 空間軸の方向。

      * `:normal`  - 最初の信号が下に（デフォルト）
      * `:reverse` - 最初の信号が上に。

# 戻り値

`::Plots.Plot`: 現在のプロットオブジェクトの上にシェーディングされたウィグル。

# 例

```julia
using Plots, WaveletsExt

# ランダム信号を生成
x = randn(16, 5)

# ----- ウィグルを構築 -----
# 既存のプロットに構築
plt = plot()
wiggle!(x)

# 指定されたプロットに構築
wiggle!(plt, x)
```

翻訳者: Nicholas Hausch – MATLABファイルは斉藤直樹によって提供されました。以前のMATLABバージョンの貢献者は、Anthony K. Booer (SLB) と Bradley Marchand (NSWC-PC) です。

改訂者: 斉藤直樹, 2018年2月5日。最新のJuliaバージョンの互換性のためにZeng Fung Liewによって維持されています。

**関連情報:** [`wiggle`](@ref)
