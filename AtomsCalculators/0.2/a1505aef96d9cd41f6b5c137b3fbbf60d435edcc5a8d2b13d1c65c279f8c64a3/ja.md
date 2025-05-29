`set_parameters!(calc, parameters) -> calc_new`

返される `calc_new` は、変異した `calc` であるか、新しいオブジェクトである可能性があります。呼び出し元は、`calc_new` が `calc` と同じオブジェクトであると仮定すべきではありません。これにより、`set_parameters!` の非変異実装が可能になります。
