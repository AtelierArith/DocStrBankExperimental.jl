```
LRP(model, rules)
LRP(model, composite)
```

モデルをレイヤーごとの関連性伝播を適用して分析します。アナライザーは、LRPルールの配列を渡すことによって作成するか、または合成物を渡すことによって作成できます。例については[`Composite`](@ref)を参照してください。

# キーワード引数

  * `normalize_output_relevance`: 出力の関連性をLRPの逆伝播を適用する前に1に設定するかどうかを選択します。文献に合わせてデフォルトは`true`です。`false`の場合、出力活性化の値が使用されます。
  * `skip_checks::Bool`: モデルがLRPと互換性があり、出力ソフトマックスを含むかどうかのチェックをスキップします。デフォルトは`false`です。
  * `verbose::Bool`: モデルチェックが失敗した場合に要約を印刷するかどうかを選択します。デフォルトは`true`です。

# 参考文献

[1] G. Montavon et al., Layer-Wise Relevance Propagation: An Overview [2] W. Samek et al., Explaining Deep Neural Networks and Beyond: A Review of Methods and Applications
