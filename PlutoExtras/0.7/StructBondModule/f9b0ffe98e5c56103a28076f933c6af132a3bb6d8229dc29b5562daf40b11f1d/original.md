```
@BondsList description block
```

Convenience macro to create a `BondsList`, which is a grouping of a various bonds (created with `@bind`) inside a table-like HTML output that can be used inside [`BondTable`](@ref). Each bond can additionally be associated to a custom description. The `block` given as second input to this macro must be a `begin` or `let` block where each line is an assignment of the type `description = bond`. The description can be anything that has a `show` method for MIME type `text/html`.

An example usage is given in the code below:

```
@BondsList "My Group of Bonds" let tv = PlutoUI.Experimental.transformed_value
	 # We use transformed_value to translate GHz to Hz in the bound variable `freq`
	"Frequency [GHz]" = @bind freq tv(x -> x * 1e9, Slider(1:10))
	md"Altitude ``h`` [m]" = @bind alt Scrubbable(100:10:200)
end
```

which will create a table-like display grouping together the bonds for the frequency `freq` and the altitude `alt`.

Unlike [`StructBond`](@ref), the output of `@BondsList` is not supposed to be bound using `@bind`, as it just groups pre-existing bonds. Also unlike `StructBond`, each row of a `BondsList` upates its corresponding bond independently from the other rows.

To help identify and differentiate a `BondsList` from a `StructBond`

See also: [`BondTable`](@ref), [`@NTBond`](@ref), [`StructBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddata`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
