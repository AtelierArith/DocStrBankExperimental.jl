Create an empty palindromic automaton of key type `T`.

The Palindromic AutoMaton (PAM, also known as the palindrome tree) is a very useful data structure for solving palindrome-related problems. A detailed introduction to PAM can be found via:

  * [Wikipedia: Palindrome Tree](https://en.wikipedia.org/wiki/Palindrome_tree)
  * [OI-Wiki: 回文树](https://oi-wiki.org/string/pam/)

To add new values into the automaton, simply use `Base.push!`.

Getters for the internal fields of the automaton are provided, including:

  * `children(pam)`: Get the children dictionary of the PAM.
  * `nodecount(pam)`: Get the number of nodes in the PAM.
  * `lastnodeindex(pam)`: Get the index of the last node of the PAM.
  * `len(pam, i)`: Get the palindrome length of the i-th node.
  * `fail(pam, i)`: Get the fail pointer of the i-th node.
  * `cnt(pam, i)`: Get the frequency count of the i-th node.

# Sample usages

  * Finding the length of the longest palindromic substring

```jldoctest
function longest_palindromic_substring(s)
    pam = PalindromicAutomaton{Char}()
    hi = 0
    for ch in s
        push!(pam, ch)
        hi = max(hi, len(pam, lastnodeindex(pam)))
    end
    return hi
end

longest_palindromic_substring("ddabababacc")

# output

7
```
