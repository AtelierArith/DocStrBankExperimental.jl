```
abstract type AbstractIrrep{G<:Group} <: Sector end
```

群 `G` の不変表現（irreducible representations）に対応するセクターの抽象スーパタイプです。ユニタリ表現を仮定するため、これらは有限群またはコンパクトリー群になります。これは、線形表現ではなく射影表現を含む可能性があることに注意してください。

これらの不変表現の実際の具体的な実装は `Irrep[G]` として取得できるか、またはその実際の名前を介して取得でき、一般的には `(asciiG)Irrep` という形式を取ります。つまり、群名のASCIIスペルの後に `Irrep` が続きます。

すべての不変表現は [`BraidingStyle`](@ref) が `Bosonic()` に等しく、したがってトリビアルなツイストを持っています。
