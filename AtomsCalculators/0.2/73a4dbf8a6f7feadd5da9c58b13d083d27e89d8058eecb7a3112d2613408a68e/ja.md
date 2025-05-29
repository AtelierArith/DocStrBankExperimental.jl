`set_state!(calc, state) -> calc_new`

返される `calc_new` は、変更された `calc` であるか、新しいオブジェクトである可能性があります。呼び出し元は、`calc_new` が `calc` と同じオブジェクトであると仮定すべきではありません。これにより、`set_state!` の非変更実装が可能になります。
