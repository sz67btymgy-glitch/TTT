import requests
import sys

def check_subdomains(domain):
    print(f"[*] Starting enumeration for: {domain}")
    # Placeholder for wordlist logic
    subdomains = ['api', 'dev', 'staging', 'mail', 'vpn']
    for sub in subdomains:
        url = f"https://{sub}.{domain}"
        try:
            requests.get(url, timeout=3)
            print(f"[+] Found active subdomain: {url}")
        except requests.ConnectionError:
            pass

if __name__ == "__main__":
    if len(sys.argv) > 1:
        target_domain = sys.argv[1]
        check_subdomains(target_domain)
    else:
        print("[-] Usage: python script.py <domain>")
