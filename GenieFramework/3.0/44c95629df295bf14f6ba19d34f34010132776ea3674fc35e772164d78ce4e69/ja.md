このマクロは、プロダクションモードまたは開発モードに基づいて静的アセット（js、アイコン、フォントなど）を構成します。

プロダクションモードでは、CDNを使用してアセットをロードします。開発モードでは、ローカルファイルシステムからアセットをロードします。

また、アプリごとにGenieDevToolsとGeniePackageManagerからルートを登録します。これは、開発目的であなたのGenie/GenieBuilderアプリでGenieDevToolsとGeniePackageManagerからのルートを利用可能にすることを意味します。

いくつかの例のルートは次のとおりです：

  * `/geniepackagemanager`
  * `/_devtools_/save`
  * `/_devtools_/up`
  * `/_devtools_/down`
  * `/_devtools_/log`
  * `/_devtools_/startrepl` など。

これらは `app_host:app_port/geniepackagemanager` などからアクセスできます。
