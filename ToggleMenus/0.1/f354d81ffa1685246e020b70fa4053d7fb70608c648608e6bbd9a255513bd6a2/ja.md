```
(maker::ToggleMenuMaker)(options[, selections])::ToggleMenu
(maker::ToggleMenuMaker)(opts::Tuple{StringVector,Vector{Char}})::ToggleMenu
(maker::ToggleMenuMaker)(header::AbstractString, options...)::ToggleMenu
```

`ToggleMenu`を作成します。

`options`は、切り替え可能な状態を持ついくつかの文字列型のベクターです。`selections`は、オプションの初期選択状態のオプションの`Vector{Char}`です。選択が`\0`の場合、メニューはナビゲーション中にその行をスキップし、切り替え可能ではなくなります。提供されない場合、メニューオプションは最初の設定から始まります。

特定のメニューに固有のヘッダーが必要な場合は、最初の引数として提供してください。これにより、`maker`のヘッダーが上書きされます（必要に応じて""にすることができます）。

メニューが終了すると、最初が選択、最後がオプションの`Tuple`の`Vector`を返します。これは、オプションとその選択を事前に構成し、メニュー関数がオプションと選択の両方を変更できるようにします。キャンセルされた場合、すべての選択は`\0`になります。

# 使用法

[`ToggleMenu`](@ref)は、[`REPL`](@extref `stdlib/REPL`)での使用のために本質的に設計されており、型シグネチャは簡単な合成のために設計されています。たとえば、これが機能します：

```julia
julia> (["option 1", "option 2"], ['a', 'b']) |> maker |> request
```

これは、オプションと選択を準備する関数とともに使用すると、より便利です。その関数が安定したら、合成を使用できます：

```julia
action = request ∘ maker ∘ prepare
```

これにより、`action(data)`は、ToggleMenu形式で提示されるデータを準備し、それを`maker`に渡し、`request`を呼び出します。

`ToggleMenus`はまた、`request`にメソッドを追加して、`ToggleMenus`のために`do`構文を可能にし、この種のワークフローを可能にします：

```julia
request(menu(options, selections)) do selected
    # ここで返された設定を処理します
end
```
