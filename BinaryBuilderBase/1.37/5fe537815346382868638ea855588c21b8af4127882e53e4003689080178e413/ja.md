`AbstractSource`は、パッケージを構築するためのソースとして使用されるものです。ソースは、ビルド環境の`${WORKSPACE}/srcdir`にインストールされます。

`AbstractSource`の具体的なサブタイプは次のとおりです：

  * [`ArchiveSource`](@ref): インターネットからダウンロードするリモートアーカイブ；
  * [`FileSource`](@ref): インターネットからダウンロードするリモートファイル；
  * [`GitSource`](@ref): クローンするリモートGitリポジトリ；
  * [`DirectorySource`](@ref): マウントするローカルディレクトリ。
