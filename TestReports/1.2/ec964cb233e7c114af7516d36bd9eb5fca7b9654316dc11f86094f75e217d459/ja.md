```
record_test_property(name::AbstractString, value)
```

テストセットに含まれるテストにプロパティを関連付けます。`name` と `value` は、JUnit XML レポート内の対応する `<testcase>` 要素を持つ `<property>` 要素に変換されます。

複数のテストプロパティをテストセット内で割り当てることができ、子テストセットは親によって定義されたテストプロパティを継承します。子テストセットが既に使用されている名前でテストプロパティを記録すると、両方のプロパティが結果のレポートに存在します。

詳細と例については、[`record_testset_property`](@ref) のドキュメントを参照してください。

関連情報: [`record_testset_property`](@ref) と [`test_properties`](@ref)。
