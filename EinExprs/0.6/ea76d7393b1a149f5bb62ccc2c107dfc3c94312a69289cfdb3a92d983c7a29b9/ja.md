```
Greedy(; metric = removedsize, choose = pop!)
```

貪欲収縮パスソルバー。メトリックを最大化する収縮を貪欲に選択します。

# キーワード

  * `metric` は候補のペアワイズテンソル収縮を評価する関数です。デフォルトは [`removedsize`](@ref) です。
  * `choose` は候補の間のペアワイズテンソル収縮を抽出する関数です。デフォルトは `pop!` を使用して `metric` を最大化する候補です。
  * `outer` `true` の場合、外積を候補として考慮します。デフォルトは `false` です。

# 実装

実装はバイナリヒープツリーを使用して候補のペアワイズテンソル収縮をソートします。その後、再帰的に、

1. `choose` 関数を使用してヒープツリーから候補を選択し抽出します。
2. 選択されたものに隣接するインデックスを含む候補の `metric` を更新します。
3. 選択されたインデックスをパスに追加し、ステップ1に戻ります。
