`SetBuilders`のメインモジュール – 命題および列挙セットのためのJuliaパッケージ

# エクスポート

  * [`@setbuild`](@ref): SetBuildersセットを構築します。
  * [`@setpkg`](@ref): Juliaモジュールからセットをロードします。
  * [`ismember`](@ref)/`in`/`∈`: オブジェクトがセットのメンバーであるかをチェックします。
  * [`describe`](@ref): セットの説明文字列を生成します。
  * [`fmap`](@ref): ドメイン内の要素をコドメイン内の要素に変換します。
  * [`bmap`](@ref): コドメイン内の要素をドメイン内の要素に変換します。
  * [`complement`](@ref)/`~`: セットの補集合演算を実行します。
  * [`SBSet`](@ref): すべてのSetBuildersセットのトップレベルタイプを表します。

# ベースモジュールを通じたエクスポート

  * `union`/`∪`: セットの和集合演算を実行します。
  * `intersection`/`∩`: セットの共通部分演算を実行します。
  * `setdiff`/`-`: セットの差集合演算を実行します。
  * `symdiff`: セットの対称差演算を実行します。
  * `push!`: EnumerableSetに要素を追加します。
  * `pop!`: EnumerableSetから要素を削除します。
