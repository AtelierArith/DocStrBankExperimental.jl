```
SMSSpamCollection(; dir=nothing)
```

The SMS Spam Collection v.1 (hereafter the corpus) is a set of SMS tagged messages  that have been collected for SMS Spam research. It contains one set of SMS messages in English of 5,574 messages, tagged according being ham (legitimate) or spam. The corpus has a total of 4,827 SMS legitimate messages (86.6%) and a total of 747 (13.4%) spam messages.

The corpus has been collected by Tiago Agostinho de Almeida (http://www.dt.fee.unicamp.br/~tiago)  and José María Gómez Hidalgo (http://www.esp.uem.es/jmgomez).

```julia-repl julia> using MLDatasets: SMSSpamCollection

julia> targets = SMSSpamCollection.targets();

julia> summary(targets) "5574-element Vector{Any}"

julia> targets[1] "ham"

julia> summary(features) "5574-element Vector{Any}"
