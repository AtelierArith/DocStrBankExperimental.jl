`AbstractDependency`はJLLパッケージのバイナリ依存関係です。依存関係はビルド環境の`${prefix}`にインストールされます。

`AbstractDependency`の具体的なサブタイプは次のとおりです。

  * [`Dependency`](@ref): パッケージをビルドし、生成されたJLLパッケージをロードするために必要なJLLパッケージです。
  * [`RuntimeDependency`](@ref): 実行時にのみ必要なJLLパッケージです。そのアーティファクトはビルド中にプレフィックスにインストールされません。
  * [`BuildDependency`](@ref): パッケージをビルドするためにのみ必要なJLLパッケージです。これは生成されたJLLパッケージの依存関係にはなりません。
  * [`HostBuildDependency`](@ref): `BuildDependency`に似ていますが、ターゲットプラットフォームの代わりにホストプラットフォームのアーティファクトをインストールします。

`AbstractDependency`のサブタイプは次の特性を定義する必要があります。

  * [`is_host_dependency`](@ref)
  * [`is_target_dependency`](@ref)
  * [`is_build_dependency`](@ref)
  * [`is_runtime_dependency`](@ref)
  * [`is_top_level_dependency`][@ref]
