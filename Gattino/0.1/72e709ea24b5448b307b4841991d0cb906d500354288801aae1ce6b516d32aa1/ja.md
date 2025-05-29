### Group <: AbstractContext

  * window::Component{:g}
  * dim::Int64{Int64, Int64}
  * margin::Pair{Int64, Int64}

`Group`は、別のコンテキストの下に保持される`Context`です。これらは、`group`を使用してスケーリングを作成し、`group!`を使用してレイヤーを作成するために使用されます。

##### 例

```
using Gattino
x = ["purple", "pink", "orange", "blue", "red", "white"]
y = [20, 40, 2, 3, 25, 49]

mycon = context(500, 500) do con::Context
    group(con, 250, 250) do firstvis::Group
        group!(firstvis, "axes") do g::Group
            Gattino.axes!(g)
        end
        group!(firstvis, "grid") do g::Group
            Gattino.grid!(g, 4)
        end
        group!(firstvis, "bars") do g::Group
            Gattino.bars!(g, x, y, "stroke-width" => 1px, "stroke" => "darkgray")
            [style!(comp, "fill" => color) for (comp, color) in zip(g.window[:children], x)]
        end
        group!(firstvis, "labels") do g::Group
            Gattino.barlabels!(g, x, "stroke-width" => 0px, "font-size" => 11pt)
        end
    end
    group(con, 250, 250, 250 => 0) do secondvis::Group
        group!(secondvis, "grid2") do g::Group
            Gattino.grid!(g, 4, "stroke" => "pink")
        end
        group!(secondvis, "line") do g::Group
            Gattino.line!(g, x, y)
        end
        group!(secondvis, "labels") do g::Group
            Gattino.gridlabels!(g, x, y, 4)
        end
    end
    group(con, 500, 250, 0 => 250) do bottomvis::Group
        group!(bottomvis, "grid3") do g::Group
            Gattino.scatter_plot!(g, [1, 2, 3], [1, 2, 3])
        end
    end
end
```

---

##### コンストラクタ

```julia
Group(name::String = gen_ref(5), width::Int64 = 1280, height::Int64 = 720,
        margin::Pair{Int64, Int64} = 0 => 0)
```
