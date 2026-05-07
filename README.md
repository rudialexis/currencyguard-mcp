# CurrencyGuard Guard Pricing — MCP Server

**The first payment-contingent FX protection server on MCP.**

CurrencyGuard enables AI agents and MCP-compatible tools to price and explain invoice-linked FX protection for SMEs — directly within agentic cross-border payment workflows.

## Endpoint

```
https://api.currencyguard.com/mcp
```

- **Transport:** Streamable HTTP
- **Authentication:** None required
- **Registry:** `com.currencyguard/guard-pricing` v1.0.0

## Tools

| Tool | Description |
|------|-------------|
| `price_guard` | Price a Guard — payment-contingent FX protection linked to a specific invoice or payable |
| `price_guard_extension` | Price an extension of an existing Guard to a later settlement date |
| `get_spot_rate` | Live indicative spot FX rate (GBPUSD, GBPEUR, EURUSD) |
| `get_forward_rate` | Indicative forward FX rate for any supported pair and tenor |
| `get_historic_best_worst` | 25 years of historic FX best/worst performance for stress modelling |
| `resolve_settlement_date` | Convert a tenor (e.g. "3M", "90 days") to a valid business settlement date |
| `list_supported_currencies` | List supported currency pairs |
| `explain_guard_product` | Product information, structure and FAQs about the Guard |

## What is the Guard?

The Guard is a **payment-contingent FX protection instrument** — not a derivative in the MiFID sense, not a vanilla option, and not an FX forward.

- **Invoice-linked:** Each Guard is tied to a specific payable or receivable. If the underlying payment does not occur, the Guard lapses — even if it has intrinsic value at that point.
- **No credit risk:** The protection cost is defined and paid upfront. No margin calls, no collateral, no credit lines required.
- **No open-ended obligations:** Unlike an FX forward, the SME has no unconditional obligation to exchange currency.
- **Upside preserved:** If the market moves favourably before settlement, the SME lets the Guard lapse and converts at the better rate.
- **Programmatically accessible:** Designed for embedded distribution — agents can price, explain and present Guard outcomes within a single workflow.

This structure makes the Guard naturally compatible with automated procurement and invoicing workflows, where FX forwards and vanilla options create credit and operational complexity that agents cannot manage.

## Quick Start

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "currencyguard": {
      "command": "npx",
      "args": ["mcp-remote", "https://api.currencyguard.com/mcp"]
    }
  }
}
```

Or use the [Smithery listing](https://smithery.ai/servers/currencyguard/guard-pricing) for one-click install.

## Example Usage

> *"I have a $500,000 invoice due in 6 months — what would it cost to protect the GBP receivable at current rates?"*

The agent pulls a live spot rate, prices the Guard, explains the protection structure, and presents the outcome — all within a single conversation.

## About CurrencyGuard

CurrencyGuard is an FX protection solution built for PSPs and SMEs. Built by a team with 100+ years of institutional FX, payments and trading technology experience.

- Website: [currencyguard.com](https://www.currencyguard.com)
- Articles: [The Missing Layer in Agentic Cross-Border Payments](https://www.currencyguard.com/insights)
- Official MCP Registry: `com.currencyguard/guard-pricing`
