# trends-agent-claude

Connect Claude to live trend data across search, social, ecommerce, news,
and developer platforms. One MCP connection, one API key, every source.

> Live trend data for AI agents. One connection. Every platform.
> Powered by [trendsmcp.ai](https://trendsmcp.ai)

## Get your free API key

1. Go to [trendsmcp.ai](https://trendsmcp.ai)
2. Enter your email, key sent instantly
3. 100 free requests per month, no credit card

[Get your free key](https://trendsmcp.ai)

## Connect Claude in 30 seconds

### Claude Desktop (Connector form, easiest)

In Claude Desktop, open the Connectors panel and add:

- **Name:** `Trends MCP`
- **Server URL:** `https://www.trendsmcp.ai/mcp`

Then sign in with your TrendsMCP account when prompted.

### Claude Desktop (manual config)

`User` → `Settings` → `Developer` → `Edit Config`. Add inside `mcpServers`:

```json
"trends-mcp": {
  "command": "npx",
  "args": [
    "-y",
    "mcp-remote",
    "https://api.trendsmcp.ai/mcp",
    "--header",
    "Authorization:${AUTH_HEADER}"
  ],
  "env": {
    "AUTH_HEADER": "Bearer YOUR_API_KEY"
  }
}
```

Config file location:

- Mac: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

Fully quit and restart Claude Desktop after saving.

### Claude Code (CLI)

```bash
claude mcp add --transport http trends-mcp https://api.trendsmcp.ai/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

Full setup walkthrough at [trendsmcp.ai/docs](https://trendsmcp.ai/docs).

## What you can ask Claude

Once connected, talk to Claude in plain English. Include the phrase
**"using TrendsMCP"** or **"via TrendsMCP"** so Claude routes to the MCP
instead of doing a web search.

- "Using TrendsMCP, show me the Google Search trend for `nvidia` over the past 5 years."
- "Via TrendsMCP, compare YouTube and TikTok trend history for `Stanley cup`."
- "Using TrendsMCP, what is the news sentiment for `Meta` over the last 6 months?"
- "Via TrendsMCP, show 12M Google Shopping growth for `running shoes`."
- "Using TrendsMCP, what are the top trending hashtags on TikTok today?"
- "Via TrendsMCP, show me Steam concurrent player data for `Elden Ring`."
- "Using TrendsMCP, what is the npm download trend for `langchain` weekly?"
- "Via TrendsMCP, what are the hottest Reddit posts right now?"

## Three tools your AI gets

- `get_trends`, historical time series for any keyword on any source
  (5 years weekly, 30 days daily where supported).
- `get_growth`, percentage change over any period (7D, 1M, 3M, 6M, 1Y,
  YTD, custom dates).
- `get_top_trends`, what is trending right now across live platform feeds.

## All data sources in one connection

One API key gives Claude every keyword source and every live feed below.

### Keyword sources (Get Trends and Get Growth)

| source | What it measures | Keyword format |
| --- | --- | --- |
| `google search` | Google search volume | Any keyword or phrase |
| `google images` | Google image search volume | Any keyword or phrase |
| `google news` | Google News search volume | Any keyword or phrase |
| `google shopping` | Google Shopping search volume | Any keyword or phrase |
| `youtube` | YouTube search volume | Any keyword or phrase |
| `tiktok` | TikTok hashtag volume | Hashtag or topic |
| `reddit` | Subreddit subscribers | Subreddit name only, no `r/` prefix |
| `amazon` | Amazon product search volume | Product name or category |
| `wikipedia` | Wikipedia page views | Article title or topic |
| `news volume` | News article mention volume | Any keyword or phrase |
| `news sentiment` | News sentiment score (positive / negative) | Any keyword or phrase |
| `app downloads` | Mobile app download estimates (Android) | Package id or app identifier |
| `npm` | npm package weekly downloads | Exact package name e.g. react |
| `steam` | Steam concurrent players (monthly) | Game display name e.g. Elden Ring |

All values are normalized to a 0 to 100 scale where the pipeline supports
it, so you can compare different sources directly.

### Live leaderboards (Get Top Trends)

Google Trends, Google News Top News, TikTok Trending Hashtags, YouTube
Trending, X (Twitter) Trending, Reddit Hot Posts, Reddit World News,
Wikipedia Trending, Amazon Best Sellers Top Rated, Amazon Best Sellers by
Category, App Store Top Free, App Store Top Paid, Google Play, Top
Websites, Spotify Top Podcasts, Steam Most Played, GitHub Trending Repos,
IMDb MOVIEmeter, Trending Books.

The source list evolves over time. Authoritative reference at
[trendsmcp.ai/docs](https://trendsmcp.ai/docs).

## Use cases for Claude

- **Research workflows.** Ask Claude to pull a 5-year trend, summarise the
  shape, and write up findings in one turn.
- **SEO and content briefs.** Have Claude compare keyword growth across
  Google, YouTube, and TikTok before deciding what to publish.
- **Investment notes.** Use news sentiment, Reddit subscriber growth, and
  Wikipedia page views as alternative data signals before writing up a
  thesis.
- **Brand and competitor tracking.** Compare share of voice across
  platforms in a single Claude conversation.
- **Live what-is-trending check.** Ask Claude what is hot on Google,
  Reddit, TikTok, or the App Store right now.

## Pricing

Free forever for 100 requests per month. Paid plans available. See
[trendsmcp.ai/pricing](https://trendsmcp.ai/pricing).

## Resources

- [Get a free API key](https://trendsmcp.ai)
- [Documentation and full reference](https://trendsmcp.ai/docs)
- [Pricing](https://trendsmcp.ai/pricing)
- [All TrendsMCP repositories](https://github.com/trendsmcp)

## Security

Never commit your API key to a public repository. Use environment variables
or your OS secret store. Keys can be rotated at any time from your
TrendsMCP dashboard. The `YOUR_API_KEY` placeholder above is a literal
string to replace with your own key after you copy the snippet locally.

## License

MIT. See [LICENSE](./LICENSE).
