```
record_testset_property(name::AbstractString, value)
```

現在のテストセットにプロパティを関連付けます。`name` と `value` は、JUnit XML レポート内の対応する `<testsuite>` 要素内の `<property>` 要素に変換されます。

複数のプロパティを1つのテストセットに追加でき、子テストセットは親によって定義されたプロパティを継承します。子テストセットがすでに設定されているプロパティを記録した場合、両方が結果のレポートに表示されます。

この関数の推奨使用法は、型が未指定のテストセット内に配置することです（例を参照）。これにより、`Pkg.test` に影響を与えず、`TestReports.test` が使用されるときにプロパティがレポートに追加されることが保証されます。これは、プロパティは `Testset` 型に `TestReports.testset_properties` メソッドが定義されている場合にのみ追加されるためであり、`TestReports` によって使用される `ReportingTestSet` も同様です。`TestReports.testset_properties` はカスタム `TestSet` 用に拡張できます。

子テストセットがこのメソッドを定義しているが親が定義していない場合、親テストセット型がレポートの動作に影響を与えない限り、`TestReport.test` が使用されるときにプロパティはレポートに含まれるべきです。ただし、これはテストされた機能ではありません。

`value` 引数は EzXML によってシリアライズ可能でなければならず、かなりの自由度を提供します。

## 例

`Pkg.test` および `TestReports.test` との互換性のためにデフォルトのテストセットを使用する：

```julia
using TestReports

# 使用されるデフォルトのテストセット、プロパティの記録呼び出しは `Pkg.test` によって無視されますが、
# JUnit XML を生成する際には使用されます。
@testset "MyTestSet" begin
    record_testset_property("ID", 42)
    record_test_property("Bool", true)
    @test 1 == 1
    @test 2 == 2
end
```

REPL で JUnit レポートをレンダリングする：

```julia
using Test, TestReports, EzXML

ts = @testset ReportingTestSet "Root" begin  # `<testsuite name="Root">` はプロパティ "foo" を持つ
    record_testset_property("foo", 1)
    record_test_property("bar", 2)

    @testset "Inner" begin  # `<testsuite name="Root/Inner">` はプロパティ "foo" を持つ
        @test 1 == 1  # `<testcase>` はプロパティ "bar" を持つ
    end

    @test 2 != 1  # `<testcase>` はプロパティ "bar" を持つ
end;

prettyprint(report(ts))
```

参照： [`record_test_property`](@ref) および [`testset_properties`](@ref).
