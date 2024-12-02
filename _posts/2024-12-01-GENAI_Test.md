---
title: "GEN AI Blogpost"
date: 2024-12-01
---

**Templating and Data Representation:** Aspect of Network Automation using a tailor made AI Chatbot just to handle this scenario

![Screenshot 2024-12-01 at 23.36.49.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ed123b20-28ee-44a4-b166-dcfdd486f6e4/daae6e7b-614b-4c03-a99d-0aac58ae3609/Screenshot_2024-12-01_at_23.36.49.png)

In today's exploration, we'll dive into the fascinating world of automation frameworks and how different data formats work together to create powerful, maintainable solutions. Drawing from extensive hands-on experience, I'll share insights into how XML, JSON, and YAML complement each other in modern automation landscapes.

**The Three Pillars of Automation Data Handling**

1. **Expression Through XML**
XML has long served as the backbone of structured data expression. Its verbose yet precise nature makes it particularly valuable for scenarios requiring strict schema validation and complex hierarchical relationships. Think of XML as the detailed blueprints of your automation architecture.
2. **Serialisation with JSON**
JSON has revolutionised data interchange in modern applications. Its lightweight structure and native compatibility with JavaScript have made it the de facto standard for API communications. Consider JSON as your data's travel format - efficient, universally understood, and easy to process.
3. **Presentation via YAML**
YAML brings human-readability to configuration management. Its clean syntax and support for complex data structures make it ideal for writing and maintaining configuration files. Think of YAML as your user interface to data representation - intuitive, clean, and maintainable.

**The Power of Integration:** Jinja2 and YAML

When we combine Jinja2's templating capabilities with YAML's presentation strengths, we unlock powerful automation possibilities:

This approach offers several advantages:

- Template reusability across different environments
- Dynamic configuration generation
- Reduced human error through automation
- Clear separation of logic and presentation

Lets take this example from Juniper Networks configuration, this is typically the blue-print on PE router and scales to some hundreds if not thousands. 

```jsx
set routing-instances CE2_L3vpn protocols bgp group CE2 type external
set routing-instances CE2_L3vpn protocols bgp group CE2 peer-as 65420
set routing-instances CE2_L3vpn protocols bgp group CE2 neighbor 172.16.2.1
set routing-instances CE2_L3vpn instance-type vrf
set routing-instances CE2_L3vpn interface xe-0/0/0:1.0
set routing-instances CE2_L3vpn route-distinguisher 192.168.0.3:12
set routing-instances CE2_L3vpn vrf-target target:65412:12
set routing-options router-id 192.168.0.3
set routing-options autonomous-system 65412
set protocols bgp group ibgp type internal
set protocols bgp group ibgp local-address 192.168.0.3
set protocols bgp group ibgp family inet-vpn unicast
set protocols bgp group ibgp neighbor 192.168.0.1
set protocols mpls label-switched-path lsp_to_pe1 to 192.168.0.1
set protocols mpls interface xe-0/0/0:0.0
set protocols ospf traffic-engineering
set protocols ospf area 0.0.0.0 interface lo0.0 passive
set protocols ospf area 0.0.0.0 interface xe-0/0/0:0.0
set protocols rsvp interface lo0.0
set protocols rsvp interface xe-0/0/0:0.0
```

When I tackled the challenge of automating configuration translations, I discovered that the secret lies not in complex programming, but in crafting a precise, well-structured prompt. Let me share my approach to building this solution.

```jsx

Generic Prompt for AI:
"You are an expert network engineer with a deep understanding 
of network configuration best practices. Your task is to generate
a configuration template and a corresponding variable file based 
on the provided configuration output. The configuration output may
include network-specific parameters such as IP addresses, 
routing protocols, device settings, and other network features.

Please perform the following tasks:

Create a Configuration Template (e.g., Jinja2 template):

Generate a template that can be used to generate network 
device configurations based on variable input.
The template should include placeholders for dynamic 
values like IP addresses, routing protocols, device names,
and any other network settings.The template should be flexible, 
reusable, and modular for various network use cases 
(e.g., BGP, OSPF, VLAN configurations).
Generate a Variable File (e.g., YAML or JSON):

Create a file that contains all the necessary configuration parameters
(variables) to feed into the template.Ensure the variable
file is structured and clear, with labels for each network
configuration item (e.g., IP addresses, interfaces, 
routing protocols, neighbor IPs, etc.).
The variables should be customizable, making
it easy for users to update their network settings as needed.

```

![Screenshot 2024-12-01 at 23.26.59.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ed123b20-28ee-44a4-b166-dcfdd486f6e4/b6a41fed-50bb-424d-96c0-d901f3b2102b/Screenshot_2024-12-01_at_23.26.59.png)

![Screenshot 2024-12-01 at 23.28.10.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ed123b20-28ee-44a4-b166-dcfdd486f6e4/b209106b-2de6-47af-8c05-96825db0ada1/Screenshot_2024-12-01_at_23.28.10.png)

  

![Screenshot 2024-12-01 at 23.28.18.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ed123b20-28ee-44a4-b166-dcfdd486f6e4/fff2cd0b-a4cf-4869-b36d-44949023f85c/Screenshot_2024-12-01_at_23.28.18.png)

This approach lets you focus on what matters – solving problems and building systems – while using tools and resources to handle the technical details. Remember, even experienced developers regularly consult documentation and use AI tools to enhance their workflow.

-Rakesh
