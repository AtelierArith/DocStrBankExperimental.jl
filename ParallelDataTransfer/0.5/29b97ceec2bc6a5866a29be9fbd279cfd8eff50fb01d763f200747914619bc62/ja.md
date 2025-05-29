include_remote(path, [workers=workers()]; module=Main) リモートワーカーで利用できないファイルを、メインノードでファイルを読み込み、テキストを解析し、`workers` にリストされたリモートワーカーでコードを評価することによって含めます。
