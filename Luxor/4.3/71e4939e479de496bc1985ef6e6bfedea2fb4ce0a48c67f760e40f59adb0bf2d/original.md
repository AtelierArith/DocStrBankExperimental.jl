```
textwrap(s::T where T<:AbstractString, width::Real, pos::Point;
    rightgutter=5,
    leading=0)
textwrap(s::T where T<:AbstractString, width::Real, pos::Point, linefunc::Function;
    rightgutter=5,
    leading=0)
```

Draw the string in `s` by splitting it at whitespace characters into lines, so that each line is no longer than `width` units. The text starts at `pos` such that the first line of text is drawn entirely below a line drawn horizontally through that position. Each line is aligned on the left side, below `pos`.

See also `textbox()`.

Optionally, before each line, execute the function `linefunc(linenumber, linetext, startpos, leading)`.

If you don't supply a value for `leading`, the font's built-in extents are used.

Text with no whitespace characters won't wrap. You can write a simple chunking function to split a string or array into chunks:

```julia
chunk(x, n) = [x[i:min(i+n-1,length(x))] for i in 1:n:length(x)]
```

For example:

```julia
textwrap(the_text, 300, boxtopleft(BoundingBox()) + 20,
    (ln, lt, sp, ht) -> begin
        c = count(t -> occursin(r"[[:punct:]]", t), split(lt, ""))
        @layer begin
            fontface("Menlo")
            sethue("darkred")
            text(string("[", c, "]"), sp + (310, 0))
        end
    end)
```

puts a count of the number of punctuation characters in each line at the end of the line.

Returns the position of what would have been the next line.
