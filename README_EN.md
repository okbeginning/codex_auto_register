<p><strong style="color:red;">⚠ 🚨 [DEPRECATED] V1 is no longer maintained due to API changes. <p>🔥 V2 (Working & Undetected) is currently closed-source and exclusively available in our community. <p>👉 Join our TG/Discord (HNUDAO Dev) to get API access: <a href="https://t.me/+inDiCrZ6ZeZiODQx">https://t.me/+inDiCrZ6ZeZiODQx</a></strong></p>

# codex_auto_register

English | [简体中文](README.md)

This is an automated OAuth authorization testing tool built on the DuckMail API. It is designed for researching high-concurrency AI API calls and identity verification mechanisms. This tool is maintained and developed by the [HNU Blockchain Association](https://github.com/HNUDAO).

For updates, bug reports, and more Web3/AI tools, join our official developer community: [Telegram Community](https://t.me/+inDiCrZ6ZeZiODQx)
<div style="text-align: left;">
  <a href="https://www.rapidproxy.io/?ref=Ttungx" target="_blank">
    <img src="assets/rapidproxy.jpg" alt="RapidProxy" width="60%">
  </a>
</div>

> [RapidProxy](https://www.rapidproxy.io/?ref=Ttungx) - Highly stable residential proxies with dynamic rotation and static dedicated IPs. Real residential IP resources help reduce risk-control issues.

---

## Sponsor HNU Blockchain Association

| Tier | Price | Benefits |
| --- | --- | --- |
| Silver Sponsor | 100U/month | Logo at the bottom of README + display on the association website |
| Gold Sponsor | 300U/month | Prominent position in the middle of README + mentor slot on the association website |
| Diamond Sponsor | 500U/month | Exclusive top placement in README + association WeChat official account post + pinned GitHub Discussion |

> WARNING: This project is for learning and research purposes only and must not be used for any commercial purpose. Users are solely responsible for all consequences arising from the use of this project.

## Credits

This project is adapted from the original project: https://github.com/adminlove520/chatgpt_register

Main differences in this repository:

- Replaced the original Codex registration email service with the DuckMail API.
- Preserved and extended the Codex protocol OAuth flow.
- Outputs Codex auth files recognizable by CLIProxyAPI v6.

## Contents

- `chatgpt_register.py`: DuckMail registration script in the repository root.
- `codex/protocol_keygen.py`: Pure HTTP Codex OAuth registration and token generation script.
- `duckmaildoc.md`: DuckMail API reference documentation (https://raw.githubusercontent.com/MoonWeSif/DuckMail/main/public/llm-api-docs.txt).
- [management.html](https://github.com/router-for-me/Cli-Proxy-API-Management-Center/releases) (auto update).

## Requirements

Root script:

```bash
pip install curl_cffi
```

Codex script:

```bash
pip install requests urllib3
```

## Configuration

This repository only commits example configuration files and does not include real configuration.

Before use, copy the examples:

```bash
copy config.example.json config.json
copy codex\config.example.json codex\config.json
```

Then fill in your own DuckMail, proxy, and CPA parameters.

## Root Script

Run:

```bash
python chatgpt_register.py
```

See `config.example.json` for the example configuration.

Main configuration items:

| Config Item | Description |
| --- | --- |
| total_accounts | Number of accounts to register |
| duckmail_api_base | DuckMail API address |
| duckmail_bearer | DuckMail Bearer Token |
| proxy | HTTP/HTTPS proxy |
| output_file | Registration result output file |
| enable_oauth | Whether to run OAuth |
| oauth_required | Whether OAuth success is required |
| upload_api_url | Optional API endpoint for uploading to CPA |
| upload_api_token | Optional CPA management API token |

## Codex Protocol Script

Run:

```bash
python codex\protocol_keygen.py
```

See `codex/config.example.json` for the example configuration.

This script will:

- Create temporary email addresses with DuckMail.
- Complete the ChatGPT registration flow.
- Execute Codex OAuth login and exchange it for a token.
- Generate token JSON files with CLIProxyAPI v6-compatible filenames.
- Optionally upload results to the CPA management API.

## Output Files

The following local files are usually generated during execution. They are already included in `.gitignore` and will not be committed to the repository:

- `config.json`
- `codex/config.json`
- `registered_accounts.txt`
- `codex/accounts.txt`
- `codex/ak.txt`
- `codex/rk.txt`
- `codex/registered_accounts.csv`
- `codex/codex_tokens/`
- `codex/codex_accounts_tokens/`

## Repository Structure

```text
chatgpt_register/
├── chatgpt_register.py
├── config.example.json
├── duckmaildoc.md
├── README.md
└── codex/
    ├── config.example.json
    ├── protocol_keygen.py
    └── README.md
```

## Notes

- A working proxy is required. Otherwise, registration, OAuth, and CPA auto-refresh may fail.
- `config.json` and `codex/config.json` should only be kept locally and should not be committed.
- If you use CLIProxyAPI, it is recommended to keep the `refresh_token` and token JSON files intact.
