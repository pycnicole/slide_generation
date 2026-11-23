# S5｜Palo Alto Networks 與 CrowdStrike：常見導入誤區與動態持續驗證邏輯

* **目標來源**：Palo Alto Networks／CrowdStrike
* **對應 Wiki 頁面**：`03`、`04`
* **原始出處**：
  * [You Want Network Segmentation, But You Need Zero Trust｜Palo Alto Networks](https://www.paloaltonetworks.com/blog/2019/01/you-want-network-segmentation-but-you-need-zero-trust/)（John Kindervag, January 17, 2019）
  * [Debunking the Myth Around Implementing Zero Trust｜Palo Alto Networks](https://live.paloaltonetworks.com/t5/community-blogs/debunking-the-myth-around-implementing-zero-trust/ba-p/255220)（John Kindervag & Scott Stevens, March 27, 2019）
  * [What is Zero Trust? - Guide to Zero Trust Security｜CrowdStrike](https://www.crowdstrike.com/en-us/cybersecurity-101/zero-trust-security/)（Ryan Terry, March 13, 2025）

## 常見導入誤區與迷思（Palo Alto Networks）

1. **誤區一：將「網路分段」等同於「零信任」**
   * 網路分段（Network segmentation）只是戰術（tactic）與工具，而非建構安全網路的戰略（strategy）。
   * 零信任解決了「為何分段」的問題：分段應「由內而外（from the inside out）」進行——先確定要保護的敏感、受規範或重要項目（資料、應用程式、資產或服務），藉此定義**保護面（Protect Surface）**，這是縮減攻擊面後最小可能的防護範圍。
2. **誤區二：僅靠 Layer 3 技術即可建立零信任**
   * 多數攻擊者皆懂得如何繞過 Layer 3／Layer 4 技術控制；真正的零信任架構必須在 Layer 7（應用層）透過分段閘道（如實體或虛擬次世代防火牆）強制執行細粒度且即時的政策控制。
3. **誤區三：認為實作零信任必然高成本且難以建置**
   * 雖然實作常被認為設定困難且成本高昂，但透過一致的方法論（例如五步驟方法）即可系統化達成，並不必然需要高昂代價。

## 動態持續驗證的運作邏輯（CrowdStrike）

* **超越單次入口驗證（Continuous Monitoring and Validation）**：在零信任架構下，組織不能僅在進入點進行一次性驗證，而必須在整個工作階段（session）期間持續監控與驗證使用者及其裝置是否仍具備適當權限與屬性，因為威脅與使用者屬性都是動態且可能快速變化的。
* **持續監控的七項核心要素**：
  1. 使用者身分與憑證類型（區分人類憑證與程式化憑證）。
  2. 憑證權限（評估各裝置關聯的權限等級）。
  3. 行為模式（分析各憑證與裝置的正常連線模式）。
  4. 端點特徵（考量硬體類型、功能與韌體版本）。
  5. 地理位置（追蹤裝置的實體位置）。
  6. 安全協定（評估認證協定、風險因素、作業系統版本與已安裝應用程式）。
  7. 事件偵測（偵測並回應可疑活動與潛在攻擊）。
* **三大運作原則與自動化情境回應（對應 NIST 800-207）**：
  * **持續驗證（Continuously Verify）**：依據即時風險評估執行風險導向條件式存取（Risk-based conditional access），並確保政策能隨工作負載、資料與位置變化快速擴展調整。
  * **限制爆炸半徑（Limit the Blast Radius）**：透過以身分為基礎的分段（Identity-based segmentation）與最低權限原則（包含服務帳號），限制潛在攻擊者在網路內的移動範圍。
  * **自動化情境蒐集與回應（Automate Context Collection and Response）**：從使用者憑證（人類與非人類／服務帳號）、工作負載（VM、容器、混合部署）、端點、網路流量與資料存取蒐集遙測數據，並透過 API 與 SIEM、SSO、身分識別提供者（IdP）及威脅情資平台整合，結合 AI／ML 分析海量遙測建立行為基線，實現即時自動化政策回應。
