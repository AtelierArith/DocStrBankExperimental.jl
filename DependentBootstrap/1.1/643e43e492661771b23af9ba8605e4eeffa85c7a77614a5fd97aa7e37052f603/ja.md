依存ブートストラップ手法のモジュール、コリン・T・バワーズによる

実装されたブートストラップ手法: 

```
- IID
- 定常
- 移動ブロック
- 循環ブロック
- NoOverlapBlock
```

実装されたブロック長選択手法: 

```
- Patton, Politis, and White (2009) 依存ブートストラップの自動ブロック長選択への修正
```

受け入れられる入力データセットのタイプ: 

```
- Vector{<:Number}
- Matrix{<:Number} （行が観測値、列が変数）
- Vector{Vector{<:Number}} （内側のベクトルの要素が観測値、外側のベクトルが変数）
- DataFrame
- TimeSeries.TimeArray{T,N} （N = 1 および N = 2 のみ）
```

追加の入力データセットタイプは簡単に追加できます。https://github.com/colintbowers/DependentBootstrap.jl で問題を開いてください。

このモジュールには、単一のエクスポートされたタイプのみがあります: 

```
- BootInput  <-- すべてのエクスポートされた関数で受け入れられるコア入力タイプ。通常はキーワードメソッドを介して構築されます。詳細については ?BootInput を参照してください。
```

すべてのエクスポートされた関数は、以下のキーワードシグネチャを示します: 

```
- exported_func(data, bootinput::BootInput)
- exported_func(data ; kwargs...)
```

ほとんどのユーザーはキーワード引数メソッドを使用して満足するでしょう。実際には、このメソッドはキーワード引数 BootInput コンストラクタをラップし、それがエクスポートされた関数 BootInput メソッドに入力されます。受け入れられるキーワードの詳細については ?BootInput を参照してください。すべてのエクスポートされた関数は、BootInput で説明された入力データセットとブートストラップ手法を使用して、適切な統計量を返します。エクスポートされた関数のリストは次のとおりです: 

```
- optblocklength <-- 入力データセットの最適なブロック長を推定
- dbootinds      <-- ブートストラップ再サンプリングインデックスのベクトルを取得
- dbootdata      <-- 再サンプリングされたデータセットのベクトルを取得
- dbootlevel1    <-- レベル 1 の再サンプリングされたブートストラップ統計のベクトルを取得
- dboot          <-- レベル 2 のブートストラップ統計を取得
- dbootlevel2    <-- dboot と同一。完全性のために含まれています
- dbootvar       <-- レベル 2 の統計を分散として設定する dboot のラッパー
- dbootconf      <-- レベル 2 の統計を信頼区間として設定する dboot のラッパー
```

このパッケージでは、レベル 1 およびレベル 2 の統計というフレーズを、ラヒリの教科書「依存データの再サンプリング手法」の第1章で議論されているのと同じ方法で使用しています。

このパッケージには MIT ライセンスがあります。詳細については関連する LICENSE.md ファイルを参照してください。
