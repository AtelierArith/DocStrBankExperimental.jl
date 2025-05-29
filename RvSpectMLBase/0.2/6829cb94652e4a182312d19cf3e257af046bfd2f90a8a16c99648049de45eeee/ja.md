返す (chunk*timeseries) は、chunk*timeseries 内のスペクトルに基づいて不良なチャンクがトリミングされたものです。現時点では NaN のチェックのみを行います。機器は独自のチェックを提供できます。入力:

  * `chunk_timeseries`: ChunkListTimeseries

オプション引数:

  * `verbose`: デバッグ情報を印刷する (false)

返す:

  * 問題のあるチャンクが削除された ChunkListTimeseries。
