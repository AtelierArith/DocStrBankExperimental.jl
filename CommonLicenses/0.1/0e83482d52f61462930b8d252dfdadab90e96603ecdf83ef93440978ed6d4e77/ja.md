```julia
struct License{ID, C<:(Union{Missing, var"#s12"} where var"#s12"<:(AbstractSet{<:AbstractString})), P<:(Union{Missing, var"#s14"} where var"#s14"<:(AbstractSet{<:AbstractString})), L<:(Union{Missing, var"#s16"} where var"#s16"<:(AbstractSet{<:AbstractString}))} <: CommonLicenses.AbstractLicense
```

法的ライセンスのメタデータ。この型のインスタンスが`Base.show`されると、内容はソフトウェアライセンスの典型的な形式で表示されます。つまり、ソフトウェアリポジトリの`LICENSE`ファイルで見るような形式です。
