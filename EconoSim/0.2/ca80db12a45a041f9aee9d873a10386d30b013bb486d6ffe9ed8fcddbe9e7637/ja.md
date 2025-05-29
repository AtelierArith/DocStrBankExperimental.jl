```
sumsy_transfer(source::Balance,
                destination::Balance,
                sumsy::SuMSy,
                amount::Real,
                timestamp::Int = 0;
                comment = "")
```

SuMSyのお金を一つのバランスシートから別のバランスシートに転送します。転送できる金額は利用可能な金額を超えることはできません。負の金額は、宛先から送信元への転送を意味します。
