```julia
struct License{ID, C<:(Union{Missing, var"#s12"} where var"#s12"<:(AbstractSet{<:AbstractString})), P<:(Union{Missing, var"#s14"} where var"#s14"<:(AbstractSet{<:AbstractString})), L<:(Union{Missing, var"#s16"} where var"#s16"<:(AbstractSet{<:AbstractString}))} <: CommonLicenses.AbstractLicense
```

Metadata for a legal license. When an instance of this type is `Base.show`n, the content is displayed in a software-license-typical format: i.e. as you would see in a software repository's `LICENSE` file.
