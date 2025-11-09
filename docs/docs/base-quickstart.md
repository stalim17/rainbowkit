# Base Quickstart for RainbowKit

Connect wallets on **Base** in minutes using RainbowKit + wagmi.

## 1) Install
```bash
npm i @rainbow-me/rainbowkit wagmi viem
import '@rainbow-me/rainbowkit/styles.css'
import { RainbowKitProvider, getDefaultConfig } from '@rainbow-me/rainbowkit'
import { WagmiProvider } from 'wagmi'
import { base, baseSepolia } from 'wagmi/chains'
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'

const config = getDefaultConfig({
  appName: 'Base dApp',
  projectId: '<WALLET_CONNECT_ID>',
  chains: [base, baseSepolia],
})

const queryClient = new QueryClient()

export function AppProviders({ children }) {
  return (
    <WagmiProvider config={config}>
      <QueryClientProvider client={queryClient}>
        <RainbowKitProvider>{children}</RainbowKitProvider>
      </QueryClientProvider>
    </WagmiProvider>
  )
}
import { ConnectButton } from '@rainbow-me/rainbowkit'
export default function Header() {
  return <ConnectButton />
}
