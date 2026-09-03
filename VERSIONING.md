# Versioning

- **Upstream base**: [brocaar/sx1302_hal](https://github.com/brocaar/sx1302_hal), tag `V2.1.0r9`.
- **This fork**: no independent release tags yet — tracked by commits on `main` since the `V2.1.0r9` baseline.

## Diff vs. upstream

Adds a runtime-configurable RX preamble length for multi-SF (ARB) channels
(`struct lgw_conf_demod_s.multisf_preamble_symb_nb` in `libloragw/inc/loragw_hal.h`),
so `concentratord4siliqs` can set it via TOML config instead of relying on the
HAL's hardcoded default of 10 symbols
(`libloragw/src/loragw_sx1302.c: sx1302_lora_modem_configure()`). A value of 0
falls back to the original hardcoded default, so upstream behavior is
unchanged unless the new field is explicitly set.

Files touched:
- `libloragw/inc/loragw_hal.h`
- `libloragw/inc/loragw_sx1302.h`
- `libloragw/src/loragw_sx1302.c`
- `libloragw/src/loragw_hal.c`
