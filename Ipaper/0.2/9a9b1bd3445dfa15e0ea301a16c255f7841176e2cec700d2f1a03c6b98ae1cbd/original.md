```julia
writelines(
    x::AbstractVector{<:AbstractString},
    f::AbstractString;
    mode,
    eof
)

```

# Arguments

  * `mode`:

Mode Description Keywords                    –––– ––––––––––– –––––––––––––––––––––––––   r    read        none                        w    write       write = true                r+   read, write read = true, write = true   w+   read, write read = true, write = true

# @seealso readlines

! `x` 需要是string，不然文件错误
