```
CrossPlatform(host::Platform, target::Platform)
```

クロスコンパイルツールチェーンを構築する際に使用される特別なプラットフォームで、`host`プラットフォームと`target`プラットフォームを含みます。両方のプラットフォームは、プラットフォームの1つをタグにエンコードすることで保持されます（例：タグのセットにプレフィックスを追加することによって、`target_arch=x86_64`、`target_os=windows`など）。

また、`host`または`target`を`AnyPlatform`として設定することもサポートしており、任意のホストだがターゲット特有のバイナリ（例えば`LinuxKernelHeaders_jll`）や、ホスト特有だが任意のターゲットのバイナリ（例えば特定の`Clang_jll`のビルド）を作成できます。この`Platform`をシリアライズされた表現（テキストおよび`Artifacts.toml`ファイルの両方）に適切に変換するためには、全体のシリアル化を基本的な`Platform`型として解析可能なものに保ちながら、`host`および`target`プラットフォームを適切にエンコードする方法を決定する必要があります。この目的のために、一般的に`host`を「ベース」プラットフォームとして選択し、タグ内に`target`をエンコードします。ただし、`host`が`AnyPlatform`である場合は、反転して`target`を「ベース」プラットフォームとして使用します。これら2つのケースを区別するために、`target`が`AnyPlatform`である場合にはセンチネルタグ`target=any`を、`host`が`AnyPlatform`である場合には`host=any`を設定します。これら2つのタグのおかげで、すべての有効な`CrossPlatform`オブジェクトは、これらのタグ（または同様に識別可能な`target_arch`/`host_os`などのタグ）の存在によって識別可能です。

「通常の」`Platform`オブジェクトを`CrossPlatform`に変換しようとした場合、`host`と`target`が等しい`CrossPlatform`オブジェクトが返されます。
