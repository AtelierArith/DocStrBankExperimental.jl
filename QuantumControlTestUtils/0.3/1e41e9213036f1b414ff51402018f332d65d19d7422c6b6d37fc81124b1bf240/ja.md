パッケージのテストスイートをサブプロセスで実行します。

```julia
test(
    file="test/runtests.jl";
    root=pwd(),
    project="test",
    code_coverage=".coverage/tracefile-%p.info",
    show_coverage=(code_coverage != "none"),
    color=<inherit>,
    compiled_modules=<inherit>,
    startup_file=<inherit>,
    depwarn=<inherit>,
    inline=<inherit>,
    check_bounds="yes",
    track_allocation=<inherit>,
    threads=<inherit>,
    genhtml=false,
    covdir="coverage"
)
```

これは、`root`にあるパッケージのテストスイートを新しいjuliaプロセス内で`include(file)`を実行することによって実行します。

これは`Pkg.test()`が行うことに似ていますが、「サンドボックス」アプローチが異なります。`Pkg.test()`は新しい一時的なサンドボックス環境を作成しますが、`test()`は`project`内の既存の環境を使用します（デフォルトでは`test`サブフォルダ）。これにより、他のパッケージの開発版に対してテストを行うことができます。`test`フォルダには`Project.toml`と`Manifest.toml`の両方のファイルが含まれている必要があります。

`test()`関数は、REPLで`test/runtests.jl`を直接含めることとは異なり、カバレッジデータとレポートを生成することができます（これはサブプロセスでテストを実行する場合にのみ可能です）。

`show_coverage`が`true`（デフォルト）として渡されると、カバレッジの概要が表示されます。さらに、`genhtml`が`true`の場合、`covdir`（`root`に対して相対的）に完全なHTMLカバレッジレポートが生成されます。これには、`genhtml`実行可能ファイル（[lcov](http://ltp.sourceforge.net/coverage/lcov.php)パッケージの一部）が必要です。`true`の代わりに、`genhtml`実行可能ファイルへのパスを渡すことも可能です。

他のすべてのキーワード引数は、サブプロセスとして実行される`julia`実行可能ファイルのそれぞれのコマンドラインフラグに対応しています。

この関数は、プロジェクトの開発REPLで公開されることを意図しています。
