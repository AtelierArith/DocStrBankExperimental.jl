julia> using .NGG  julia> mkngg(                         :f, #fname                         [                                 Argument(:a, nothing, Unset()),                                 Argument(:b, nothing, Unset())                         ],  # args                         Argument[], # kwargs                         :(a + b) #expression                 )  f = (a, b;) -> a + b

julia> ans(1, 2)  3
