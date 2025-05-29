```
effects::Effects
```

メソッド呼び出しの計算効果を表します。

効果は、分析されているメソッドのプログラム特性を表す異なる効果ビットの組み合わせです。これらは、次の意味を持つ `Bool` または `UInt8` ビットとして表されます。

  * `consistent::UInt8`:

      * `ALWAYS_TRUE`: このメソッドは一貫して返すか終了することが保証されています。
      * `ALWAYS_FALSE`: このメソッドは一貫して返すか終了しない可能性があり、この効果特性に関してさらなる分析は必要ありません。この結論はどうせ洗練されることはありません。
      * `CONSISTENT_IF_NOTRETURNED`: このメソッドの `:consistent`-cy は、戻り値が新しく割り当てられた可変オブジェクトを含まない場合に `ALWAYS_TRUE` に洗練される可能性があります。
      * `CONSISTENT_IF_INACCESSIBLEMEMONLY`: このメソッドの `:consistent`-cy は、`:inaccessiblememonly` が証明された場合に `ALWAYS_TRUE` に洗練される可能性があります。
  * `effect_free::UInt8`:

      * `ALWAYS_TRUE`: このメソッドは外部から見える意味的副作用がありません。
      * `ALWAYS_FALSE`: このメソッドは外部から見える意味的副作用がないとは限らず、この効果特性に関してさらなる分析は必要ありません。この結論はどうせ洗練されることはありません。
      * `EFFECT_FREE_IF_INACCESSIBLEMEMONLY`: このメソッドの `:effect-free`-ness は、`:inaccessiblememonly` が証明された場合に `ALWAYS_TRUE` に洗練される可能性があります。
  * `nothrow::Bool`: このメソッドは例外をスローしないことが保証されています。このメソッドの実行が `MethodError` や類似の例外を引き起こす可能性がある場合、このメソッドは `:nothrow` と見なされません。ただし、`StackOverflowError` や `InterruptException` のような環境依存のエラーはこの効果によってモデル化されていないため、`StackOverflowError` を引き起こす可能性のあるメソッドは必ずしも `:nothrow` を汚染する必要はありません（ただし、通常は `:terminates` も汚染すべきです）。
  * `terminates::Bool`: このメソッドは終了することが保証されています。
  * `notaskstate::Bool`: このメソッドは現在のタスクにバインドされた状態にアクセスせず、したがって観察可能な動作を変更することなく別のタスクに移動できます。現在、これは `noyield` も含むことを意味します。なぜなら、yielding は現在のタスクの状態を変更するからです。ただし、将来的にはこれが分割される可能性があります。
  * `inaccessiblememonly::UInt8`:

      * `ALWAYS_TRUE`: このメソッドは外部からアクセス可能な可変メモリにアクセスまたは変更しません。この状態は LLVM の `inaccessiblememonly` 関数属性に対応します。
      * `ALWAYS_FALSE`: このメソッドは外部からアクセス可能な可変メモリにアクセスまたは変更する可能性があります。
      * `INACCESSIBLEMEM_OR_ARGMEMONLY`: このメソッドは外部からアクセス可能な可変メモリにアクセスまたは変更しませんが、呼び出し引数によって指される可変メモリにアクセスまたは変更する可能性があります。呼び出し引数が不変であることが知られている場合、これは後に `ALWAYS_TRUE` に洗練される可能性があります。この状態は LLVM の `inaccessiblemem_or_argmemonly` 関数属性に対応します。
  * `noub::UInt8`:

      * `ALWAYS_TRUE`: このメソッドは未定義の動作を実行しないことが保証されています（任意の入力に対して）。
      * `ALWAYS_FALSE`: このメソッドは未定義の動作を実行する可能性があります。
      * `NOUB_IF_NOINBOUNDS`: このメソッドは、呼び出し元が `@inbounds` コンテキストを設定または伝播しない場合、未定義の動作を実行しないことが保証されています。

    未定義の動作は技術的にはこのメソッドが他の効果の主張（例えば `:consistent` や `:effect_free`）を侵害する原因となる可能性がありますが、これをモデル化しておらず、未定義の動作が存在しないことを前提としています。
  * `nonoverlayed::UInt8`:

      * `ALWAYS_TRUE`: このメソッドは [overlayed method table](@ref OverlayMethodTable) に定義されたメソッドを呼び出さないことが保証されています。
      * `CONSISTENT_OVERLAY`: このメソッドはオーバーレイされたメソッドを呼び出す可能性がありますが、すべてのオーバーレイされたメソッドはその非オーバーレイされた元の対応物と `:consistent` です（`Base.@assume_effects` の正確な定義については[@ref]を参照してください）。
      * `ALWAYS_FALSE`: このメソッドはオーバーレイされたメソッドを呼び出す可能性があります。
  * `nortcall::Bool`: このメソッドは `Core.Compiler.return_type` を呼び出さず、このメソッドが呼び出す可能性のある他のメソッドも `Core.Compiler.return_type` を呼び出さないことが保証されています。

上記の表現は内部実装の詳細に過ぎず、将来的に変更される可能性があることに注意してください。これらの特性の定義についての詳細な説明は [`Base.@assume_effects`](@ref) を参照してください。

抽象解釈に沿って、各ステートメントでの `Effects` はローカルに分析され、分析されたメソッド全体の効果を表す単一のグローバル `Effects` にマージされます（`merge_effects!` の実装を参照）。各効果特性は `ALWAYS_TRUE`/`true` で初期化され、その後 `ALWAYS_FALSE`/`false` に遷移します。現在のフロー非感受性分析設計内では、各ステートメントでのローカル分析によって検出された効果は通常、保守的にグローバルな結論を汚染します。

## Effects の `show` 出力のキー:

出力は、次の順序で異なる効果特性の状態を表します。

1. `consistent` (`c`):

      * `+c` (緑): `ALWAYS_TRUE`
      * `-c` (赤): `ALWAYS_FALSE`
      * `?c` (黄): `CONSISTENT_IF_NOTRETURNED` および/または `CONSISTENT_IF_INACCESSIBLEMEMONLY`
2. `effect_free` (`e`):

      * `+e` (緑): `ALWAYS_TRUE`
      * `-e` (赤): `ALWAYS_FALSE`
      * `?e` (黄): `EFFECT_FREE_IF_INACCESSIBLEMEMONLY`
3. `nothrow` (`n`):

      * `+n` (緑): `true`
      * `-n` (赤): `false`
4. `terminates` (`t`):

      * `+t` (緑): `true`
      * `-t` (赤): `false`
5. `notaskstate` (`s`):

      * `+s` (緑): `true`
      * `-s` (赤): `false`
6. `inaccessiblememonly` (`m`):

      * `+m` (緑): `ALWAYS_TRUE`
      * `-m` (赤): `ALWAYS_FALSE`
      * `?m` (黄): `INACCESSIBLEMEM_OR_ARGMEMONLY`
7. `noub` (`u`):

      * `+u` (緑): `true`
      * `-u` (赤): `false`
      * `?u` (黄): `NOUB_IF_NOINBOUNDS`
8. `:nonoverlayed` (`o`):

      * `+o` (緑): `ALWAYS_TRUE`
      * `-o` (赤): `ALWAYS_FALSE`
      * `?o` (黄): `CONSISTENT_OVERLAY`
9. `:nortcall` (`r`):

      * `+r` (緑): `true`
      * `-r` (赤): `false`
