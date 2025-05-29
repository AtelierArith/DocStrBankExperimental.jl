SiennaシステムからPSS/E形式へのエクスポートを実行するための構造体。`PowerFlowData`からのオプションの更新を含め、`System`とPSS/Eバージョンから構築し、関連する新しいデータで`update_exporter`を使用して更新し、`write_export`でエクスポートを実行します。`<name>.raw`ファイルと、PSS/Eの命名規則に従うために行われた変換を含む`<name>_export_metadata.json`ファイルを書き出します。これにより、PowerSystems.jlを使用して名前を復元しながらラウンドトリップを実行できます。

# 引数:

  * `base_system::PSY.System`: エクスポートされるシステム。後の更新により、電力フロー関連の値が変更される可能性がありますが、システムの基本的な構造は変更されません。
  * `psse_version::Symbol`: 対象とするPSS/Eのバージョン。`PSSE_EXPORT_SUPPORTED_VERSIONS`のいずれかでなければなりません。
  * `write_comments::Bool` = false: スラッシュの後の最初の行とグループ境界で、仕様には含まれていないが慣習的な注釈を追加するかどうか。
  * `name::AbstractString = "export"`: エクスポートの基本名。
  * `step::Any = nothing`: 基本エクスポート名に追加するオプションのステップデータ。ユーザーはステップデータの更新に責任を持ちます。ステップデータが`nothing`の場合は使用されず、タプルまたはベクターの場合は'*'で結合され、その他の場合は'*'の後に結合されます。
  * `overwrite::Bool = false`: 既存のエクスポートを静かに上書きする場合は`true`、既存の結果が見つかった場合にエラーをスローする場合は`false`。
