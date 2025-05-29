コールバック関数のプロトタイプは、ある要素のセットを別の要素に置き換えるためのものです。

これは、適応後に呼び出すことができる置換ルーチンによって使用されます。既存の有効なフォレストの要素が変更されるときに使用されます。このコールバックにより、ユーザーは新しいフォレストの要素を変更することができ、これらは古いフォレストの要素と比較して、洗練された、粗くされた、または同じである可能性があります。

要素が洗練されている場合、*refine* と *num_outgoing* は 1 になり、*num_incoming* は子の数になります。ファミリーが粗くされている場合、*refine* は -1 になり、*num_outgoing* はファミリーのメンバーの数になり、*num_incoming* は 1 になります。要素が削除されている場合、*refine* と *num_outgoing* は 1 になり、*num_incoming* は 0 になります。それ以外の場合、*refine* は 0 になり、*num_outgoing* と *num_incoming* は両方とも 1 になります。

# 引数

  * `forest_old`:[in] 適応されるフォレスト
  * `forest_new`:[in] *forest_old* から新たに構築されたフォレスト
  * `which_tree`:[in] *first_outgoing* と *first_incoming* を含むローカルツリー
  * `ts`:[in] ツリーの eclass スキーム
  * `refine`:[in] -1 は *forest_old* のファミリーが粗くされたことを示し、0 は要素が触れられていないことを示し、1 は要素が洗練されたことを示し、-2 は要素が削除されたことを示します。[`t8_forest_adapt_t`](@ref) の戻り値を参照してください。
  * `num_outgoing`:[in] アウトゴーイング要素の数。
  * `first_outgoing`:[in] 最初のアウトゴーイング要素のツリー内ローカルインデックス。0 <= first*outgoing < which*tree->num_elements
  * `num_incoming`:[in] インカミング要素の数。
  * `first_incoming`:[in] 最初のインカミング要素のツリー内ローカルインデックス。0 <= first*incom < new*which*tree->num*elements

# 参照

[`t8_forest_iterate_replace`](@ref)
