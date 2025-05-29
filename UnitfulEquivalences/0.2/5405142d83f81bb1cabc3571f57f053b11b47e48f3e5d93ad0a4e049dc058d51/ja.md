```
Spectral(; frequency=:linear, wavelength=:linear, wavenumber=:linear)
```

光子のエネルギーをその（線形または角）周波数、波長、および波数に関連付ける等価性。線形または角の量に変換するかどうかは、オプションのキーワード引数によって決定され、すべての量のデフォルトは`:linear`です。

等価な量は、$E = hf = ħω = hc/λ = ħc/ƛ = hcν̃ = ħck$という関係に従って変換されます。ここで、

  * $$
    E
    $$

    は光子エネルギー、
  * $$
    f
    $$

    は（時間的）周波数（`frequency=:linear`）、
  * $$
    ω
    $$

    は角周波数（`frequency=:angular`）、
  * $$
    λ
    $$

    は波長（`wavelength=:linear`）、
  * $$
    ƛ
    $$

    は角（縮小）波長（`wavelength=:angular`）、
  * $$
    ν̃
    $$

    は分光波数（`wavenumber=:linear`）、
  * $$
    k
    $$

    は角波数（`wavelength=:angular`）、
  * $$
    h
    $$

    はプランク定数、
  * $$
    ħ
    $$

    は縮小プランク定数、
  * $$
    c
    $$

    は真空中の光速です。

# 例

```jldoctest
julia> uconvert(u"nm", 13.6u"eV", Spectral()) # 水素をイオン化するために必要な光子の波長
91.16485178911785 nm

julia> uconvert(u"Hz", 589u"nm", Spectral(frequency=:angular)) # ナトリウムD線の角周波数
3.1980501991661345e15 Hz
```
