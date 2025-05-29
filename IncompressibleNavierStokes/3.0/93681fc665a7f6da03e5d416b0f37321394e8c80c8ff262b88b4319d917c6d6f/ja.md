リアルタイムで解をプロットするためのプロセッサ。

キーワード引数：

  * `plot`: プロット関数。
  * `nupdate`: `nupdate` タイムステップごとに解を表示。
  * `displayfig`: 開始時に図を表示。
  * `screen`: `nothing` の場合、デフォルトの表示を使用。 `GLMakie.screen()` を使用すると、MATLABのように別々のウィンドウで複数のプロットを表示できます（`GLMakie.closeall()` も参照）。
  * `displayupdates`: 更新ごとに図を表示（CairoMakieを使用している場合）。
  * `sleeptime`: `sleeptime` は毎回の更新でスリープし、Makie にプロットを更新する時間を与えます。スリープをスキップするには、これを `nothing` に設定します。

追加の `kwargs` は `plot` 関数に渡されます。
