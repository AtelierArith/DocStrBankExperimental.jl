```
mirror_tarball(registry, upstreams::AbstractVector, static_dir::String; kwargs...)
```

レジストリ `registry` のすべての静的コンテンツを生成します。

ビルド後、すべての静的コンテンツデータは `static_dir` に保存されます：

  * `/registries`: このサーバーのレジストリ UUID のマップとその現在のツリーハッシュ
  * `/registry/$uuid/$hash`: 指定されたツリーハッシュでのレジストリ UUID のタールボール
  * `/package/$uuid/$hash`: 指定されたツリーハッシュでのパッケージ UUID のタールボール
  * `/artifact/$hash`: 指定されたツリーハッシュでのアーティファクトのタールボール

環境変数 `JULIA_NUM_THREADS` を設定してマルチスレッドを有効にします。

# キーワードパラメータ

  * `http_parameters::Dict{Symbol, Any}`: リソースを取得する際に `HTTP.get` に渡す必要がある任意のパラメータ。
  * `packages::AbstractVector{Package}`: 保存する必要があるパッケージのセットを手動で作成し指定します。これを使用して、完全なストレージの一部のみをビルドできます。パッケージ情報をビルドする方法については [`read_packages`](@ref read_packages) を確認してください。
  * `show_progress::Bool`: 追加の進行メーターを表示するには `true` にします。デフォルトは `true` です。
  * `skip_duration::Real`: 次回の試行まで `/failed_resources.txt` にリストされたリソースをスキップする時間（時間単位）を指定します。デフォルトは `24` 時間です。
