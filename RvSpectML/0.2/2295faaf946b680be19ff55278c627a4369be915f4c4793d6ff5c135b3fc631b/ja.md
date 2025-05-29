bin*times*consecutive( times, n ) は、n 回の連続したビンからの平均時間を計算します（bin*consecutive*spectra に合わせて）。floor(length(times)/n) 要素を返します。

警告: 単に連続した時間を取得するため、一部のビンは近くで取得されていないスペクトルからのものかもしれません。TODO: タイムスタンプに注意を払うバージョンを作成します。
