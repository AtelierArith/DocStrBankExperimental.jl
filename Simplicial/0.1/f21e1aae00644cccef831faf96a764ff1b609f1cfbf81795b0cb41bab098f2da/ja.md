iszero(p) は、擬似多項式が実際にゼロであるかどうかを判断します。言い換えれば、p.x と p.y が非空の交差を持っていることを意味します。この実装は、明らかに単純な実装よりも若干速いことに注意してください。= !isempty(intersect(p.x,p.y))
